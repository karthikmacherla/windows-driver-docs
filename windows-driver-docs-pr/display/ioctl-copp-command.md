---
title: IOCTL\_COPP\_Command control code
description: Performs an operation on a COPP DirectX VA device.
keywords: ["IOCTL_COPP_Command control code Display Devices"]
topic_type:
- apiref
api_name:
- IOCTL_COPP_Command
api_type:
- NA
ms.date: 01/05/2018
---

# IOCTL\_COPP\_Command control code


Performs an operation on a COPP DirectX VA device.

## <span id="ddk_ioctl_copp_command_gg"></span><span id="DDK_IOCTL_COPP_COMMAND_GG"></span>


### <span id="Input_Parameters"></span><span id="input_parameters"></span><span id="INPUT_PARAMETERS"></span>Input Parameters

The [**VIDEO\_REQUEST\_PACKET**](/windows-hardware/drivers/ddi/video/ns-video-_video_request_packet) (VRP) **InputBuffer** contains information passed from the display driver. For example, the display driver can pass a pointer to a COPP\_IO\_InputBuffer structure defined as follows:

```cpp
typedef struct {
    PVOID* ppThis;
    PVOID InputBuffer;
    HRESULT phr;
} COPP_IO_InputBuffer;
```

The **ppThis** member points to a pointer to the COPP DirectX VA device object on which an operation is performed. The **InputBuffer** member is set to a pointer to a [**DXVA\_COPPCommand**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_coppcommand) structure that describes the COPP command to perform. The **phr** member should be set to the value returned from the [*COPPCommand*](./coppcommand.md) function.

### <span id="Output_Parameters"></span><span id="output_parameters"></span><span id="OUTPUT_PARAMETERS"></span>Output Parameters

None

### <span id="I_O_Status_Block"></span><span id="i_o_status_block"></span><span id="I_O_STATUS_BLOCK"></span>I/O Status Block

The miniport driver does not set the **Information** member of the [**STATUS\_BLOCK**](/windows-hardware/drivers/ddi/video/ns-video-_status_block) structure.

## Requirements

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Version</p></td>
<td align="left"><p>This section applies only to Windows Server 2003 with SP1 and later, and Windows XP with SP2 and later.</p></td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[*COPPCommand*](./coppcommand.md)

[**DXVA\_COPPCommand**](/windows-hardware/drivers/ddi/dxva/ns-dxva-_dxva_coppcommand)

 

