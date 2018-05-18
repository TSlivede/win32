---
title: Authentication-Level Constants
description: The authentication-level constants represent authentication levels passed to various run-time functions.
ms.assetid: 'b8bb2517-e1a0-4607-a672-259f8686fc3e'
topic_type:
- apiref
api_name:
- RPC_C_AUTHN_LEVEL_DEFAULT
- RPC_C_AUTHN_LEVEL_NONE
- RPC_C_AUTHN_LEVEL_CONNECT
- RPC_C_AUTHN_LEVEL_CALL
- RPC_C_AUTHN_LEVEL_PKT
- RPC_C_AUTHN_LEVEL_PKT_INTEGRITY
- RPC_C_AUTHN_LEVEL_PKT_PRIVACY
api_location:
- Rpcdce.h
api_type:
- HeaderDef
---

# Authentication-Level Constants

The authentication-level constants represent authentication levels passed to various run-time functions. These levels are listed in order of increasing authentication. Each new level adds to the authentication provided by the previous level. If the RPC run-time library does not support the specified level, it automatically upgrades to the next higher supported level.



| Constant                                                                                                                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span id="RPC_C_AUTHN_LEVEL_DEFAULT"></span><span id="rpc_c_authn_level_default"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_DEFAULT**</dt> </dl>                    | Uses the default authentication level for the specified authentication service.<br/>                                                                                                                                                                                                                                                                                                                                                    |
| <span id="RPC_C_AUTHN_LEVEL_NONE"></span><span id="rpc_c_authn_level_none"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_NONE**</dt> </dl>                             | Performs no authentication.<br/>                                                                                                                                                                                                                                                                                                                                                                                                        |
| <span id="RPC_C_AUTHN_LEVEL_CONNECT"></span><span id="rpc_c_authn_level_connect"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_CONNECT**</dt> </dl>                    | Authenticates only when the client establishes a relationship with a server.<br/>                                                                                                                                                                                                                                                                                                                                                       |
| <span id="RPC_C_AUTHN_LEVEL_CALL"></span><span id="rpc_c_authn_level_call"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_CALL**</dt> </dl>                             | Authenticates only at the beginning of each remote procedure call when the server receives the request. Does not apply to remote procedure calls made using the connection-based protocol sequences (those that start with the prefix "ncacn"). If the protocol sequence in a binding handle is a connection-based protocol sequence and you specify this level, this routine instead uses the RPC\_C\_AUTHN\_LEVEL\_PKT constant.<br/> |
| <span id="RPC_C_AUTHN_LEVEL_PKT"></span><span id="rpc_c_authn_level_pkt"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_PKT**</dt> </dl>                                | Authenticates only that all data received is from the expected client. Does not validate the data itself.<br/>                                                                                                                                                                                                                                                                                                                          |
| <span id="RPC_C_AUTHN_LEVEL_PKT_INTEGRITY"></span><span id="rpc_c_authn_level_pkt_integrity"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_PKT\_INTEGRITY**</dt> </dl> | Authenticates and verifies that none of the data transferred between client and server has been modified.<br/>                                                                                                                                                                                                                                                                                                                          |
| <span id="RPC_C_AUTHN_LEVEL_PKT_PRIVACY"></span><span id="rpc_c_authn_level_pkt_privacy"></span><dl> <dt>**RPC\_C\_AUTHN\_LEVEL\_PKT\_PRIVACY**</dt> </dl>       | Includes all previous levels, and ensures clear text data can only be seen by the sender and the receiver. In the local case, this involves using a secure channel. In the remote case, this involves encrypting the argument value of each remote procedure call.<br/>                                                                                                                                                                 |



## Remarks

Regardless of the value specified by the constant, **ncalrpc** always uses RPC\_C\_AUTHN\_LEVEL\_PKT\_PRIVACY.

## Requirements



|                                     |                                                                                     |
|-------------------------------------|-------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�2000 Professional \[desktop apps only\]<br/>                          |
| Minimum supported server<br/> | Windows�2000 Server \[desktop apps only\]<br/>                                |
| Header<br/>                   | <dl> <dt>Rpcdce.h</dt> </dl> |



## See also

<dl> <dt>

[**RpcBindingInqAuthInfo**](rpcbindinginqauthinfo.md)
</dt> <dt>

[**RpcBindingSetAuthInfo**](rpcbindingsetauthinfo.md)
</dt> <dt>

[**RpcMgmtInqDefaultProtectLevel**](rpcmgmtinqdefaultprotectlevel.md)
</dt> <dt>

[**RpcBindingInqAuthClient**](rpcbindinginqauthclient.md)
</dt> <dt>

[**RpcBindingInqAuthClientEx**](rpcbindinginqauthclientex.md)
</dt> <dt>

[**RpcBindingSetAuthInfoEx**](rpcbindingsetauthinfoex.md)
</dt> <dt>

[**RpcBindingInqAuthInfoEx**](rpcbindinginqauthinfoex.md)
</dt> </dl>

�

�




