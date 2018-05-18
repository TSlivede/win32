---
Description: 'Opens an HTTP connection to an HTTP resource.'
ms.assetid: '5207e873-44c0-4eeb-9db8-d8b69432070c'
title: 'IWinHttpRequest::Open method'
---

# IWinHttpRequest::Open method

The **Open** method opens an HTTP connection to an HTTP resource.

## Syntax


```C++
HRESULT Open(
  [in]�����������BSTR ���Method,
  [in]�����������BSTR ���Url,
  [in, optional]�VARIANT Async
);
```



## Parameters

<dl> <dt>

*Method* \[in\]
</dt> <dd>

Specifies the [*HTTP verb*](glossary.md#term-http-verb) used for the **Open** method, such as "GET" or "PUT". Always use uppercase as some servers ignore lowercase *HTTP verb*s.

</dd> <dt>

*Url* \[in\]
</dt> <dd>

Specifies the name of the resource. This must be an absolute URL.

</dd> <dt>

*Async* \[in, optional\]
</dt> <dd>

Indicates whether to open in asynchronous mode.



| Value                                                                                                                                                         | Meaning                                                                                                                                                                                           |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="VARIANT_FALSE"></span><span id="variant_false"></span><dl> <dt>**VARIANT\_FALSE**</dt> </dl> | Opens the HTTP connection in synchronous mode. A call to [**Send**](iwinhttprequest-send.md) does not return until [WinHTTP](about-winhttp.md) has completely received the response.<br/> |
| <span id="VARIANT_TRUE"></span><span id="variant_true"></span><dl> <dt>**VARIANT\_TRUE**</dt> </dl>    | Opens the HTTP connection in asynchronous mode.<br/>                                                                                                                                        |



�

</dd> </dl>

## Return value

The return value is **S\_OK** on success or an error value otherwise.

## Remarks

This method opens a connection to the resource identified in *Url* using the [*HTTP verb*](glossary.md#term-http-verb) given in *Method*.

> [!Note]  
> For Windows�XP and Windows�2000, see the [Run-Time Requirements](winhttp-start-page.md) section of the WinHTTP Start Page.

�

## Examples

The following example shows how to open an HTTP connection, send an HTTP request, and read the response text.


```C++
#include <windows.h>
#include <stdio.h>
#include <objbase.h>

#include "httprequest.h"

#pragma comment(lib, "ole32.lib")
#pragma comment(lib, "oleaut32.lib")

// IID for IWinHttpRequest.
const IID IID_IWinHttpRequest =
{
  0x06f29373,
  0x5c5a,
  0x4b54,
  {0xb0, 0x25, 0x6e, 0xf1, 0xbf, 0x8a, 0xbf, 0x0e}
};

int main()
{
    // Variable for return value
    HRESULT    hr;

    // Initialize COM
    hr = CoInitialize( NULL );

    IWinHttpRequest *  pIWinHttpRequest = NULL;

    BSTR            bstrResponse = NULL;
    VARIANT         varFalse;
    VARIANT         varEmpty;

    CLSID           clsid;

    VariantInit(&amp;varFalse);
    V_VT(&amp;varFalse)   = VT_BOOL;
    V_BOOL(&amp;varFalse) = VARIANT_FALSE;

    VariantInit(&amp;varEmpty);
    V_VT(&amp;varEmpty) = VT_ERROR;

    hr = CLSIDFromProgID(L"WinHttp.WinHttpRequest.5.1",
                           &amp;clsid);

    if (SUCCEEDED(hr))
    {
        hr = CoCreateInstance(clsid,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IWinHttpRequest,
                              (void **)&amp;pIWinHttpRequest);
    }
    if (SUCCEEDED(hr))
    {
        // Open WinHttpRequest.
        BSTR bstrMethod  = SysAllocString(L"GET");
        BSTR bstrUrl = SysAllocString(L"http://microsoft.com");
        hr = pIWinHttpRequest->Open(bstrMethod,
                                    bstrUrl,
                                    varFalse);
        SysFreeString(bstrMethod);
        SysFreeString(bstrUrl);
    }
    if (SUCCEEDED(hr))
    {
        // Send Request.
        hr = pIWinHttpRequest->Send(varEmpty);
    }
    if (SUCCEEDED(hr))
    {
        // Get Response text.
        hr = pIWinHttpRequest->get_ResponseText(&amp;bstrResponse);
    }
    if (SUCCEEDED(hr))
    {
        // Print the response to a console.
        wprintf(L"%.256s",bstrResponse);
    }

    // Release memory.
    if (pIWinHttpRequest)
        pIWinHttpRequest->Release();
    if (bstrResponse)
        SysFreeString(bstrResponse);

    CoUninitialize();
    return 0;
}

```



The following scripting example shows how to open an HTTP connection, send an HTTP request, and read the response text.


```JScript
// Instantiate a WinHttpRequest object.
var WinHttpReq = new ActiveXObject("WinHttp.WinHttpRequest.5.1");

// Initialize an HTTP request.  
WinHttpReq.Open("GET", "http://www.microsoft.com", false);

// Send the HTTP request.
WinHttpReq.Send(); 

// Display the response text.
WScript.Echo( WinHttpReq.ResponseText);
```



## Requirements



|                                     |                                                                                            |
|-------------------------------------|--------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�XP, Windows�2000 Professional with SP3 \[desktop apps only\]<br/>            |
| Minimum supported server<br/> | Windows Server�2003, Windows�2000 Server with SP3 \[desktop apps only\]<br/>         |
| Redistributable<br/>          | WinHTTP 5.0 and Internet Explorer 5.01 or later on Windows�XP and Windows�2000.<br/> |
| IDL<br/>                      | <dl> <dt>HttpRequest.idl</dt> </dl> |
| Library<br/>                  | <dl> <dt>Winhttp.lib</dt> </dl>     |
| DLL<br/>                      | <dl> <dt>Winhttp.dll</dt> </dl>     |



## See also

<dl> <dt>

[**IWinHttpRequest**](iwinhttprequest-interface.md)
</dt> <dt>

[**WinHttpRequest**](winhttprequest.md)
</dt> <dt>

[WinHTTP Versions](winhttp-versions.md)
</dt> </dl>

�

�



