﻿---
Description: 'Applies software skinning to the target vertices based on the current matrices.'
ms.assetid: '4858dfd4-dc0d-4852-9165-8ae1b40386d4'
title: 'ID3DXSkinInfo::UpdateSkinnedMesh method'
---

# ID3DXSkinInfo::UpdateSkinnedMesh method

Applies software skinning to the target vertices based on the current matrices.

## Syntax


```C++
HRESULT UpdateSkinnedMesh(
  [in] const D3DXMATRIX *pBoneTransforms,
  [in] const D3DXMATRIX *pBoneInvTransposeTransforms,
  [in]       LPCVOID    pVerticesSrc,
  [in]       PVOID      pVerticesDst
);
```



## Parameters

<dl> <dt>

*pBoneTransforms* \[in\]
</dt> <dd>

Type: **const [**D3DXMATRIX**](d3dxmatrix.md)\***

Bone transform matrix.

</dd> <dt>

*pBoneInvTransposeTransforms* \[in\]
</dt> <dd>

Type: **const [**D3DXMATRIX**](d3dxmatrix.md)\***

Inverse transpose of the bone transform matrix.

</dd> <dt>

*pVerticesSrc* \[in\]
</dt> <dd>

Type: **[**LPCVOID**](winprog.windows_data_types)**

Pointer to the buffer containing the source vertices.

</dd> <dt>

*pVerticesDst* \[in\]
</dt> <dd>

Type: **[**PVOID**](winprog.windows_data_types)**

Pointer to the buffer containing the destination vertices.

</dd> </dl>

## Return value

Type: **[**HRESULT**](455d07e9-52c3-4efb-a9dc-2955cbfd38cc)**

If the method succeeds, the return value is D3D\_OK. If the method fails, the return value can be D3DERR\_INVALIDCALL.

## Remarks

When used to skin vertices with two position elements, this method skins the second position element with the inverse of the bone instead of the bone itself.

## Requirements



|                    |                                                                                        |
|--------------------|----------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>D3DX9Mesh.h</dt> </dl> |
| Library<br/> | <dl> <dt>D3dx9.lib</dt> </dl>   |



## See also

<dl> <dt>

[ID3DXSkinInfo](id3dxskininfo.md)
</dt> </dl>

 

 



