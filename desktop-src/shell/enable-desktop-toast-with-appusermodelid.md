---
Description: This topic shows you how to create a shortcut for your app, assign it an AppUserModelID, and install it in the Start screen.
title: How to enable desktop toast notifications through an AppUserModelID
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# How to enable desktop toast notifications through an AppUserModelID

This topic shows you how to create a shortcut for your app, assign it an [AppUserModelID](appids.md), and install it in the Start screen. We strongly recommend that you do this in the Windows Installer rather than in your app's code. Without a valid shortcut installed in the Start screen or in **All Programs**, you cannot raise a toast notification from a desktop app.

> [!Note]  
> The example methods used in this topic are taken from the [Desktop toast sample](http://go.microsoft.com/fwlink/p/?linkid=242463).

 

## What you need to know

### Technologies

-   COM

### Prerequisites

-   Libraries
    -   C++: Runtime.object.lib
    -   C\#: Windows.Winmd
-   C\#: Windows API Code Pack for Microsoft .NET Framework
-   A version of Microsoft Visual Studio that supports at least Windows 8

## Instructions

### Step 1: Prepare the shortcut to be created

This example first determines the path of the user's app data folder through the [**GetEnvironmentVariable**](https://msdn.microsoft.com/1d4cc328-12e6-4aae-9f58-58675116ad54) function. It then composes the full path to the shortcut, determines that a shortcut of that name does not already exist at that location, and passes that information to another method which creates and installs the shortcut.

Note that the shortcut can be deployed per-user or per-app.


```C++
HRESULT DesktopToastsApp::TryCreateShortcut()
{
    wchar_t shortcutPath[MAX_PATH];
    DWORD charWritten = GetEnvironmentVariable(L"APPDATA", shortcutPath, MAX_PATH);
    HRESULT hr = charWritten > 0 ? S_OK : E_INVALIDARG;

    if (SUCCEEDED(hr))
    {
        errno_t concatError = wcscat_s(shortcutPath, ARRAYSIZE(shortcutPath), L"\\Microsoft\\Windows\\Start Menu\\Programs\\Desktop Toasts App.lnk");
 
        hr = concatError == 0 ? S_OK : E_INVALIDARG;
        if (SUCCEEDED(hr))
        {
            DWORD attributes = GetFileAttributes(shortcutPath);
            bool fileExists = attributes < 0xFFFFFFF;

            if (!fileExists)
            {
                hr = InstallShortcut(shortcutPath);  // See step 2.
            }
            else
            {
                hr = S_FALSE;
            }
        }
    }
    return hr;
}
```



### Step 2: Create the shortcut and install it in the Start screen

This example also retrieves the shortcut's property store and sets the required [System.AppUserModel.ID](https://msdn.microsoft.com/07858b3c-e601-40ec-a87a-d66612d5473a) property from a previously defined variable, `AppID`.


```C++
HRESULT DesktopToastsApp::InstallShortcut(_In_z_ wchar_t *shortcutPath)
{
    wchar_t exePath[MAX_PATH];
    
    DWORD charWritten = GetModuleFileNameEx(GetCurrentProcess(), nullptr, exePath, ARRAYSIZE(exePath));

    HRESULT hr = charWritten > 0 ? S_OK : E_FAIL;
    
    if (SUCCEEDED(hr))
    {
        ComPtr<IShellLink> shellLink;
        hr = CoCreateInstance(CLSID_ShellLink, nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&amp;shellLink));

        if (SUCCEEDED(hr))
        {
            hr = shellLink->SetPath(exePath);
            if (SUCCEEDED(hr))
            {
                hr = shellLink->SetArguments(L"");
                if (SUCCEEDED(hr))
                {
                    ComPtr<IPropertyStore> propertyStore;

                    hr = shellLink.As(&amp;propertyStore);
                    if (SUCCEEDED(hr))
                    {
                        PROPVARIANT appIdPropVar;
                        hr = InitPropVariantFromString(AppId, &amp;appIdPropVar);
                        if (SUCCEEDED(hr))
                        {
                            hr = propertyStore->SetValue(PKEY_AppUserModel_ID, appIdPropVar);
                            if (SUCCEEDED(hr))
                            {
                                hr = propertyStore->Commit();
                                if (SUCCEEDED(hr))
                                {
                                    ComPtr<IPersistFile> persistFile;
                                    hr = shellLink.As(&amp;persistFile);
                                    if (SUCCEEDED(hr))
                                    {
                                        hr = persistFile->Save(shortcutPath, TRUE);
                                    }
                                }
                            }
                            PropVariantClear(&amp;appIdPropVar);
                        }
                    }
                }
            }
        }
    }
    return hr;
}
```



## Remarks

As an alternative to the approach shown in this topic, you can use a framework such as the Windows Installer XML (WiX) to generate the shortcut and deploy it as part of the Windows Installer. In that case, this code should be included in the MSI rather than in the app's code. For more information, see the sample WiX configuration file included with the [Sending toast notifications from desktop apps](http://go.microsoft.com/fwlink/p/?linkid=242463) sample.

## Related topics

<dl> <dt>

[Quickstart: Sending a toast notification from the desktop](quickstart-sending-desktop-toast.md)
</dt> <dt>

[Sending toast notifications from desktop apps sample](http://go.microsoft.com/fwlink/p/?linkid=242463)
</dt> <dt>

[Application User Model IDs (AppUserModelIDs)](appids.md)
</dt> <dt>

[How to: Install the Windows Installer XML (WiX) Tools](https://msdn.microsoft.com/windows/desktop/d02c70e2-3eea-46ea-b100-53e776852dde)
</dt> <dt>

[Sending toast notifications from desktop apps sample](http://go.microsoft.com/fwlink/p/?linkid=231503)
</dt> <dt>

[Toast notifications sample](http://go.microsoft.com/fwlink/p/?linkid=231503)
</dt> <dt>

[Toast XML schema](https://msdn.microsoft.com/06ae9be6-c573-4b35-83e0-371ed8299e33)
</dt> <dt>

[Toast notification overview](https://msdn.microsoft.com/14A07FCE-D631-4bad-AB99-305B703713E6)
</dt> <dt>

[Quickstart: Sending a toast notification](https://msdn.microsoft.com/098DF37C-4D40-4499-B809-CCB651DA1CBA)
</dt> <dt>

[Quickstart: Sending a toast push notification](https://www.bing.com/search?q=Quickstart:+Sending+a+toast+push+notification)
</dt> <dt>

[Guidelines and checklist for toast notifications](002951E3-3D2D-454A-A0B7-DAA5C1E7178A)
</dt> <dt>

[How to add images to a toast template](https://www.bing.com/search?q=How+to+add+images+to+a+toast+template)
</dt> <dt>

[How to check toast notification settings](https://www.bing.com/search?q=How+to+check+toast+notification+settings)
</dt> <dt>

[How to choose and use a toast template](098DF37C-4D40-4499-B809-CCB651DA1CBA)
</dt> <dt>

[How to handle activation from a toast notification](https://msdn.microsoft.com/74BA3513-0A52-46a0-8769-ED58ABE7C05A)
</dt> <dt>

[How to opt in for toast notifications](https://msdn.microsoft.com/809CDD36-6DE1-4de0-88B2-62B46CAFDB28)
</dt> <dt>

[Choosing a toast template](1A437614-4259-426b-8E3F-CA57368B2E7A)
</dt> <dt>

[Toast audio options](12185879-1F9B-4bdc-99E7-A6F2F62806CB)
</dt> </dl>

 

 


