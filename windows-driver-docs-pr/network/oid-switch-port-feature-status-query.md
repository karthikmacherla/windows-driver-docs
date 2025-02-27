---
title: OID_SWITCH_PORT_FEATURE_STATUS_QUERY
description: The protocol edge of the Hyper-V extensible switch issues an object identifier (OID) method request of OID_SWITCH_PORT_FEATURE_STATUS_QUERY to obtain custom status information from an extension about an extensible switch port.
ms.date: 08/08/2017
keywords: 
 -OID_SWITCH_PORT_FEATURE_STATUS_QUERY Network Drivers Starting with Windows Vista
---

# OID\_SWITCH\_PORT\_FEATURE\_STATUS\_QUERY


The protocol edge of the Hyper-V extensible switch issues an object identifier (OID) method request of OID\_SWITCH\_PORT\_FEATURE\_STATUS\_QUERY to obtain custom status information from an extension about an extensible switch port. This information is known as *feature status* information. The format of this information is defined by the independent software vendor (ISV).

After a successful return from this OID method request, the **InformationBuffer** member of the [**NDIS\_OID\_REQUEST**](/windows-hardware/drivers/ddi/oidrequest/ns-oidrequest-ndis_oid_request) structure contains a pointer to a buffer. This buffer contains the following data:

-   An [**NDIS\_SWITCH\_PORT\_FEATURE\_STATUS\_PARAMETERS**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_parameters) structure that specifies the parameters for the type of feature status information to be returned.

-   An [**NDIS\_SWITCH\_PORT\_FEATURE\_STATUS\_CUSTOM**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_custom) structure that contains the feature status information for the extensible switch port.

## Remarks

For guidelines on how to handle an OID set request of OID\_SWITCH\_PORT\_FEATURE\_STATUS\_QUERY, see [Managing Custom Port Feature Status Information](./managing-custom-port-feature-status-information.md).

### Return Status Codes

The extension returns one of the following status codes for the OID method request of OID\_SWITCH\_PORT\_FEATURE\_STATUS\_QUERY.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Status Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NDIS_STATUS_SUCCESS</p></td>
<td><p>The OID request completed successfully.</p></td>
</tr>
<tr class="even">
<td><p>NDIS_STATUS_INVALID_LENGTH</p></td>
<td><p>The length of the information buffer is too small to return the feature status information as well as the <a href="/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_custom" data-raw-source="[&lt;strong&gt;NDIS_SWITCH_PORT_FEATURE_STATUS_CUSTOM&lt;/strong&gt;](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_custom)"><strong>NDIS_SWITCH_PORT_FEATURE_STATUS_CUSTOM</strong></a> and <a href="/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_parameters" data-raw-source="[&lt;strong&gt;NDIS_SWITCH_PORT_FEATURE_STATUS_PARAMETERS&lt;/strong&gt;](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_parameters)"><strong>NDIS_SWITCH_PORT_FEATURE_STATUS_PARAMETERS</strong></a> structures. The underlying miniport edge of the extensible switch sets the <strong>DATA.METHOD_INFORMATION.BytesNeeded</strong> member in the <a href="/windows-hardware/drivers/ddi/ndis/ns-ndis-_ndis_oid_request" data-raw-source="[&lt;strong&gt;NDIS_OID_REQUEST&lt;/strong&gt;](/windows-hardware/drivers/ddi/oidrequest/ns-oidrequest-ndis_oid_request)"><strong>NDIS_OID_REQUEST</strong></a> structure to the minimum buffer size that is required.</p></td>
</tr>
<tr class="odd">
<td><p>NDIS_STATUS_FAILURE</p></td>
<td><p>The request failed for other reasons.</p></td>
</tr>
</tbody>
</table>

 

## Requirements

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Version</p></td>
<td><p>Supported in NDIS 6.30 and later.</p></td>
</tr>
<tr class="even">
<td><p>Header</p></td>
<td>Ntddndis.h (include Ndis.h)</td>
</tr>
</tbody>
</table>

## See also


****
[**NDIS\_OID\_REQUEST**](/windows-hardware/drivers/ddi/oidrequest/ns-oidrequest-ndis_oid_request)

[**NDIS\_SWITCH\_PORT\_FEATURE\_STATUS\_CUSTOM**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_custom)

[**NDIS\_SWITCH\_PORT\_FEATURE\_STATUS\_PARAMETERS**](/windows-hardware/drivers/ddi/ntddndis/ns-ntddndis-_ndis_switch_port_feature_status_parameters)

[**NDIS\_SWITCH\_PORT\_PROPERTY\_TYPE**](/windows-hardware/drivers/ddi/ntddndis/ne-ntddndis-_ndis_switch_port_property_type)

