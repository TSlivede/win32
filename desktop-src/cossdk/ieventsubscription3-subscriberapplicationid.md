---
Description: 'The application GUID of the subscriber.'
ms.assetid: '46c91cae-ca31-4eac-baa8-d36910917f0f'
title: 'IEventSubscription3::SubscriberApplicationID property'
---

# IEventSubscription3::SubscriberApplicationID property

The application GUID of the subscriber.

This property is read/write.

## Syntax


```C++
HRESULT put_SubscriberApplicationID(
  [in]����������BSTR bstrSubscriberApplicationID
);

HRESULT get_SubscriberApplicationID(
  [out, retval]�BSTR *pbstrSubscriberApplicationID
);
```



## Property value

A string containing the GUID of the subscriber application.

## Error codes

This method can return the standard return values E\_INVALIDARG, E\_OUTOFMEMORY, E\_UNEXPECTED, E\_FAIL, and S\_OK.

## Requirements



|                                     |                                                            |
|-------------------------------------|------------------------------------------------------------|
| Minimum supported client<br/> | Windows�2000 Professional \[desktop apps only\]<br/> |
| Minimum supported server<br/> | Windows�2000 Server \[desktop apps only\]<br/>       |



## See also

<dl> <dt>

[**IEventSubscription3**](ieventsubscription3.md)
</dt> </dl>

�

�



