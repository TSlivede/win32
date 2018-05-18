﻿---
Description: 'Gets a string.'
ms.assetid: '49388582-a110-4aa2-90ab-2282b59da951'
title: 'ID3DXBaseEffect::GetString method'
---

# ID3DXBaseEffect::GetString method

Gets a string.

## Syntax


```C++
HRESULT GetString(
  [in]  D3DXHANDLE hParameter,
  [out] LPCSTR     *ppString
);
```



## Parameters

<dl> <dt>

*hParameter* \[in\]
</dt> <dd>

Type: **[D3DXHANDLE](dx9-graphics-reference-effects-constants.md)**

Unique identifier. See [Handles (Direct3D 9)](handles.md).

</dd> <dt>

*ppString* \[out\]
</dt> <dd>

Type: **[**LPCSTR**](winprog.windows_data_types)\***

Returns a string identified by hParameter.

</dd> </dl>

## Return value

Type: **[**HRESULT**](455d07e9-52c3-4efb-a9dc-2955cbfd38cc)**

If the method succeeds, the return value is D3D\_OK. If the method fails, the return value can be D3DERR\_INVALIDCALL.

## Requirements



|                    |                                                                                          |
|--------------------|------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX9Shader.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3dx9.lib</dt> </dl>     |



## See also

<dl> <dt>

[ID3DXBaseEffect](id3dxbaseeffect.md)
</dt> <dt>

[**SetString**](id3dxbaseeffect--setstring.md)
</dt> </dl>

 

 



