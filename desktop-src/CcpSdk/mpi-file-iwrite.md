---
Description: 'TBD.'
audience: developer
author: 'REDMOND\\danlep'
manager: 'REDMOND\\timlt'
ms.assetid: '1f2c71dd-8f06-4a96-bb54-449c9bcdcfa1'
ms.prod: 'windows-server-dev'
ms.technology: 'compute-cluster-pack'
ms.tgt_platform: multiple
title: 'MPI\_File\_iwrite function'
---

# MPI\_File\_iwrite function

TBD

## Syntax


```C++
int MPIAPI MPI_File_iwrite(
  ������MPI_File ����file,
  _In_��void ��������*buf,
  ������int ���������count,
  ������MPI_Datatype datatype,
  _Out_�MPI_Request �*request
);
```



## Parameters

<dl> <dt>

*file* 
</dt> <dd>

TBD

</dd> <dt>

*buf* \[in\]
</dt> <dd>

TBD

</dd> <dt>

*count* 
</dt> <dd>

TBD

</dd> <dt>

*datatype* 
</dt> <dd>

TBD

</dd> <dt>

*request* \[out\]
</dt> <dd>

TBD

</dd> </dl>

## Return value

TBD

## Fortran

``` syntax
MPI_FILE_IWRITE(FH, BUF, COUNT, DATATYPE, REQUEST, IERROR)
    <type> BUF(*)
    INTEGER FH, COUNT, DATATYPE, REQUEST, IERROR
```

## Requirements



|                    |                                                                                                                                                                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Product<br/> | HPC Pack 2012 MS-MPI Redistributable Package, HPC Pack 2008 R2 MS-MPI Redistributable Package, HPC Pack 2008 MS-MPI Redistributable Package or HPC Pack 2008 Client Utilities<br/> |
| Header<br/>  | <dl> <dt>Mpi.h; </dt> <dt>Mpif.h</dt> </dl>                                           |
| Library<br/> | <dl> <dt>Msmpi.lib</dt> </dl>                                                                                                     |
| DLL<br/>     | <dl> <dt>Msmpi.dll</dt> </dl>                                                                                                     |



## See also

<dl> <dt>

[MPI File Functions](mpi-file-functions.md)
</dt> </dl>

�

�



