---
title: PSN\_SETACTIVE notification code
description: Notifies a page that it is about to be activated. This notification code is sent in the form of a WM\_NOTIFY message.
ms.assetid: 0cf918b7-9f0d-4dec-8df1-a1d2d8ac6463
keywords:
- PSN_SETACTIVE notification code Windows Controls
topic_type:
- apiref
api_name:
- PSN_SETACTIVE
api_location:
- Prsht.h
api_type:
- HeaderDef
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# PSN\_SETACTIVE notification code

Notifies a page that it is about to be activated. This notification code is sent in the form of a [**WM\_NOTIFY**](wm-notify.md) message.


```C++
PSN_SETACTIVE 

    lppsn = (LPPSHNOTIFY) lParam; 
```



## Parameters

<dl> <dt>

*lParam* 
</dt> <dd>

Pointer to a [**PSHNOTIFY**](/windows/win32/Prsht/ns-prsht-_pshnotify?branch=master) structure that contains information about the notification code. This structure contains an [**NMHDR**](/windows/win32/richedit/ns-richedit-_nmhdr?branch=master) structure as its first member, **hdr**. The **hwndFrom** member of this **NMHDR** structure contains the handle to the property sheet. The **lParam** member of the **PSHNOTIFY** structure does not contain any information.

</dd> </dl>

## Return value

Returns zero to accept the activation, or -1 to activate the next or the previous page (depending on whether the user clicked the **Next** or **Back** button). To set the activation to a particular page, return the resource identifier of the page.

## Remarks

The PSN\_SETACTIVE notification code is sent before the page is visible. An application can use this notification code to initialize data in the page.

> [!Note]  
> The property sheet is in the process of manipulating the list of pages when the PSN\_SETACTIVE notification code is sent. Do not attempt to add, remove, or insert pages while handling this notification code. Doing so will have unpredictable results.

 

To set the return value, the dialog box procedure for the page must use the [**SetWindowLong**](https://msdn.microsoft.com/library/windows/desktop/ms633591) function with the DWL\_MSGRESULT value, and the dialog box procedure must return **TRUE**.

## Requirements



|                                     |                                                                                    |
|-------------------------------------|------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                     |
| Minimum supported server<br/> | Windows Server 2003 \[desktop apps only\]<br/>                               |
| Header<br/>                   | <dl> <dt>Prsht.h</dt> </dl> |



 

 




