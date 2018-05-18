﻿---
Description: 'This class is the event type class for PnP events. The following syntax is simplified from MOF code.'
ms.assetid: '01e9a8bb-3f54-4e20-b4db-1b4bba745d4f'
title: 'SystemConfig\_PnP class'
---

# SystemConfig\_PnP class

This class is the event type class for PnP events.

The following syntax is simplified from MOF code.

## Syntax

``` syntax
[EventType(22), EventTypeName("PnP")]
class SystemConfig_PnP : SystemConfig
{
  uint32 IDLength;
  uint32 DescriptionLength;
  uint32 FriendlyNameLength;
  string DeviceID;
  string DeviceDescription;
  string FriendlyName;
};
```

## Members

The **SystemConfig\_PnP** class has these types of members:

-   [Properties](#properties)

### Properties

The **SystemConfig\_PnP** class has these properties.

<dl> <dt>

**DescriptionLength**
</dt> <dd> <dl> <dt>

Data type: **uint32**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(2)
</dt> </dl>

Length, in characters, of the DeviceDescription string.

</dd> <dt>

**DeviceDescription**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(5), StringTermination("NullTerminated"), Format("w")
</dt> </dl>

Description of the PnP device.

</dd> <dt>

**DeviceID**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(4), StringTermination("NullTerminated"), Format("w")
</dt> </dl>

Identifies the PnP device.

</dd> <dt>

**FriendlyName**
</dt> <dd> <dl> <dt>

Data type: **string**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(6), StringTermination("NullTerminated"), Format("w")
</dt> </dl>

Name of the PnP device to use in a user interface.

</dd> <dt>

**FriendlyNameLength**
</dt> <dd> <dl> <dt>

Data type: **uint32**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(3)
</dt> </dl>

Length, in characters, of the FriendlyName string.

</dd> <dt>

**IDLength**
</dt> <dd> <dl> <dt>

Data type: **uint32**
</dt> <dt>

Access type: Read-only
</dt> <dt>

Qualifiers: WmiDataId(1)
</dt> </dl>

Length, in characters, of the DeviceID string.

</dd> </dl>

## Requirements



|                                     |                                                      |
|-------------------------------------|------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>       |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/> |



## See also

<dl> <dt>

[**SystemConfig**](systemconfig.md)
</dt> </dl>

 

 



