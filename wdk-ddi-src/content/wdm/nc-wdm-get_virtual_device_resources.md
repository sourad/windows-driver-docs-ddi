---
UID: NC:wdm.GET_VIRTUAL_DEVICE_RESOURCES
title: GET_VIRTUAL_DEVICE_RESOURCES (wdm.h)
description: The GetResources routine returns the resources that the PCI Express (PCIe) physical function (PF) requires in order to enable virtualization on a device that supports the single root I/O virtualization (SR-IOV) interface.
tech.root: PCI
ms.date: 01/19/2023
keywords: ["GET_VIRTUAL_DEVICE_RESOURCES callback"]
ms.keywords: GET_VIRTUAL_DEVICE_RESOURCES, GetResources, GetResources routine, PCI.getresources, wdm/GetResources
req.header: wdm.h
req.include-header: Wdm.h
req.target-type: Desktop
req.target-min-winverclnt: Supported in Windows Server 2012 and later versions of Windows.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: PASSIVE_LEVEL
targetos: Windows
req.typenames: WDI_TYPE_PMK_NAME, *PWDI_TYPE_PMK_NAME
req.product: Windows 10 or later.
f1_keywords:
 - GET_VIRTUAL_DEVICE_RESOURCES
 - wdm/GET_VIRTUAL_DEVICE_RESOURCES
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - Wdm.h
api_name:
 - GET_VIRTUAL_DEVICE_RESOURCES
---

## -description

The **GetResources** routine returns the resources that the PCI Express (PCIe) physical function (PF) requires in order to enable virtualization on a device that supports the single root I/O virtualization (SR-IOV) interface.

## -parameters

### -param Context [in, out]

A pointer to interface-specific context information. The caller passes the value that is passed as the **Context** member of the [**PCI_VIRTUALIZATION_INTERFACE**](./ns-wdm-pci_virtualization_interface.md) structure for the interface.

### -param CapturedBusNumbers [out]

A pointer to a caller-supplied variable in which this routine returns a UINT8 value. This value specifies the number of PCIe buses that have been captured for use by the SR-IOV PF of the device.

## -remarks

A PCIe device typically consumes resources on a single PCI bus.  The PCI driver assigns a device to a PCI bus by writing the bus number into the Secondary Bus Number register and Subordinate Bus Number register in the upstream bridge port. This port is a PCI-to-PCI bridge within a PCIe root port or a PCIe switch port.

A device that supports the SR-IOV interface may create more virtual functions than can be accommodated on the PCI bus on which the device is connected.  In these situations, the upstream bridge port must be configured to capture one or more unused PCI buses.  This is done by writing a larger value to the port's Subordinate Bus Number register.

A device that supports the SR-IOV interface  must capture PCI buses if at least one of the following is true:

- The device has more than eight total functions (PFs and VFs) and the device does not support the Alternative Routing Interpretation (ARI) option of the PCI Express 3.0 specification.

- The device supports ARI and has more than eight total functions, but the upstream bridge port does not support ARI.

- The device supports ARI and has more than 256 functions, and the upstream bridge port does  support ARI.

Regardless of ARI support, each captured bus can support 256 functions.

If the device needs more PCIe Requestor IDs (RIDs) in order to enable all  of its VFs, the PCI bus driver does the following:

1. Writes the device's bus number into the PCIe Secondary Bus Number register.

1. Writes a value that is larger than the device's bus number into the PCIe Subordinate Bus Number register.

The difference between these two register values represents the number of captured bus numbers.

The **GetResources** routine is provided by the **GUID_PCI_VIRTUALIZATION_INTERFACE** interface.

## -see-also

[**PCI_VIRTUALIZATION_INTERFACE**](./ns-wdm-pci_virtualization_interface.md)
