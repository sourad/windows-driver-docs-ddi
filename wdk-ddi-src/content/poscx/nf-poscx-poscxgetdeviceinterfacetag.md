---
UID: NF:poscx.PosCxGetDeviceInterfaceTag
title: PosCxGetDeviceInterfaceTag function (poscx.h)
description: PosCxGetDeviceInterfaceTag returns the device interface tag that is set in PosCxOpen.
old-location: pos\poscxgetdeviceinterfacetag.htm
tech.root: pos
ms.date: 02/23/2018
keywords: ["PosCxGetDeviceInterfaceTag function"]
ms.keywords: PosCxGetDeviceInterfaceTag, PosCxGetDeviceInterfaceTag function, pos.poscxgetdeviceinterfacetag, poscx/PosCxGetDeviceInterfaceTag
req.header: poscx.h
req.include-header: Poscx.h
req.target-type: Windows
req.target-min-winverclnt: 
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
req.irql: 
targetos: Windows
req.typenames: 
req.product: Windows 10 or later.
f1_keywords:
 - PosCxGetDeviceInterfaceTag
 - poscx/PosCxGetDeviceInterfaceTag
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - poscx.h
api_name:
 - PosCxGetDeviceInterfaceTag
---

# PosCxGetDeviceInterfaceTag function


## -description

PosCxGetDeviceInterfaceTag returns the device interface tag that is set in <a href="/windows-hardware/drivers/ddi/poscx/nf-poscx-poscxopen">PosCxOpen</a>.

## -parameters

### -param fileObject [in]


      A handle to a framework file object that identifies the caller, usually acquired with <a href="/windows-hardware/drivers/ddi/wdfrequest/nf-wdfrequest-wdfrequestgetfileobject">WdfRequestGetFileObject</a>.

## -returns

      The device interface tag value.

## -see-also

<a href="/windows-hardware/drivers/ddi/poscx/nf-poscx-poscxopen">PosCxOpen</a>
