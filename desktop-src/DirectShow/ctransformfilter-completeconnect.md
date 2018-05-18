---
Description: 'The CompleteConnect method completes a pin connection.'
ms.assetid: 'b687d2ee-4aee-4fae-bc2f-23ee037d0e6d'
title: 'CTransformFilter.CompleteConnect method'
---

# CTransformFilter.CompleteConnect method

The `CompleteConnect` method completes a pin connection.

## Syntax


```C++
virtual HRESULT CompleteConnect(
  �PIN_DIRECTION direction,
  �IPin ���������*pReceivePin
);
```



## Parameters

<dl> <dt>

*direction* 
</dt> <dd>

Member of the [**PIN\_DIRECTION**](pin-direction.md) enumerated type, specifying which pin on the filter is making the connection.

</dd> <dt>

*pReceivePin* 
</dt> <dd>

Pointer to the [**IPin**](ipin.md) interface of the other pin in this connection attempt.

</dd> </dl>

## Return value

Returns S\_OK.

## Remarks

The [**CTransformInputPin::CompleteConnect**](ctransforminputpin-completeconnect.md) and [**CTransformOutputPin::CompleteConnect**](ctransformoutputpin-completeconnect.md) methods call this method during the pin connection process. This method does nothing in the base class, but the derived class can override it.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Transfrm.h (include Streams.h)</dt> </dl>                                                                                  |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CTransformFilter Class**](ctransformfilter.md)
</dt> </dl>

�

�



