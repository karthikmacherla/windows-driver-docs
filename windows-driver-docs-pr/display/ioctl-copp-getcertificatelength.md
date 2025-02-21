---
title: IOCTL\_COPP\_GetCertificateLength control code
description: Returns the size, in bytes, of the certificate used by the graphics hardware.
keywords: ["IOCTL_COPP_GetCertificateLength control code Display Devices"]
topic_type:
- apiref
api_name:
- IOCTL_COPP_GetCertificateLength
api_type:
- NA
ms.date: 01/05/2018
---

# IOCTL\_COPP\_GetCertificateLength control code


Returns the size, in bytes, of the certificate used by the graphics hardware.

## <span id="ddk_ioctl_copp_getcertificatelength_gg"></span><span id="DDK_IOCTL_COPP_GETCERTIFICATELENGTH_GG"></span>


### <span id="Input_Parameters"></span><span id="input_parameters"></span><span id="INPUT_PARAMETERS"></span>Input Parameters

The [**VIDEO\_REQUEST\_PACKET**](/windows-hardware/drivers/ddi/video/ns-video-_video_request_packet) (VRP) **InputBuffer** contains information passed from the display driver. For example, the display driver can pass a pointer to a COPP\_IO\_InputBuffer structure defined as follows:

```cpp
typedef struct {
    PVOID* ppThis;
    PVOID InputBuffer;
    HRESULT phr;
} COPP_IO_InputBuffer;
```

The **ppThis** member points to a pointer to the COPP DirectX VA device object that is used to retrieve the size of the hardware certificate. The **InputBuffer** member is not required. The **phr** member should be set to the value returned from the [*COPPGetCertificateLength*](./coppgetcertificatelength.md) function.

### <span id="Output_Parameters"></span><span id="output_parameters"></span><span id="OUTPUT_PARAMETERS"></span>Output Parameters

The miniport driver returns a pointer to a ULONG-typed variable in the VRP **OutputBuffer**. The variable holds the size of the hardware certificate.

### <span id="I_O_Status_Block"></span><span id="i_o_status_block"></span><span id="I_O_STATUS_BLOCK"></span>I/O Status Block

The miniport driver sets the **Information** member of the [**STATUS\_BLOCK**](/windows-hardware/drivers/ddi/video/ns-video-_status_block) structure to sizeof(ULONG).

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


[*COPPGetCertificateLength*](./coppgetcertificatelength.md)

 

