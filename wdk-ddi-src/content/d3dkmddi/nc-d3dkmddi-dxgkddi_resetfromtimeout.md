---
UID: NC:d3dkmddi.DXGKDDI_RESETFROMTIMEOUT
title: DXGKDDI_RESETFROMTIMEOUT (d3dkmddi.h)
description: The DxgkDdiResetFromTimeout function resets the graphics processing unit (GPU) after a hardware timeout occurs and guarantees that the GPU is not writing or reading any memory by the time that DxgkDdiResetFromTimeout returns.
old-location: display\dxgkddiresetfromtimeout.htm
ms.date: 05/10/2018
keywords: ["DXGKDDI_RESETFROMTIMEOUT callback function"]
ms.keywords: DXGKDDI_RESETFROMTIMEOUT, DXGKDDI_RESETFROMTIMEOUT callback, DmFunctions_de82b888-dc3d-40b6-a3c3-360254efb972.xml, DxgkDdiResetFromTimeout, DxgkDdiResetFromTimeout callback function [Display Devices], d3dkmddi/DxgkDdiResetFromTimeout, display.dxgkddiresetfromtimeout
req.header: d3dkmddi.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows Vista
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
tech.root: display
req.typenames: 
f1_keywords:
 - DXGKDDI_RESETFROMTIMEOUT
 - d3dkmddi/DXGKDDI_RESETFROMTIMEOUT
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - d3dkmddi.h
api_name:
 - DXGKDDI_RESETFROMTIMEOUT
product:
 - Windows
---

# DXGKDDI_RESETFROMTIMEOUT callback function


## -description

The <i>DxgkDdiResetFromTimeout</i> function resets the graphics processing unit (GPU) after a hardware timeout occurs and guarantees that the GPU is not writing or reading any memory by the time that <i>DxgkDdiResetFromTimeout</i> returns.

## -parameters

### -param hAdapter [in]

A handle to a context block that is associated with a display adapter. The display miniport driver previously provided this handle to the Microsoft DirectX graphics kernel subsystem in the <i>MiniportDeviceContext</i> output parameter of the <a href="/windows-hardware/drivers/ddi/dispmprt/nc-dispmprt-dxgkddi_add_device">DxgkDdiAddDevice</a> function.

## -returns

<i>DxgkDdiResetFromTimeout</i> returns STATUS_SUCCESS to indicate that the driver handled the call successfully; otherwise, the operating system bug checks and causes a restart.

## -remarks

The GPU scheduler calls <i>DxgkDdiResetFromTimeout</i> when it detects that a hardware time-out occurred. The time-out is typically a delayed response to a preempt request. <i>DxgkDdiResetFromTimeout</i> should reset the GPU. 

For more information about time-outs in this situation, see <a href="/windows-hardware/drivers/display/thread-synchronization-and-tdr">Thread Synchronization and TDR</a>.

<i>DxgkDdiResetFromTimeout</i> should be made pageable.

## -see-also

<a href="/windows-hardware/drivers/ddi/dispmprt/nc-dispmprt-dxgkddi_add_device">DxgkDdiAddDevice</a>



<a href="/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_releaseswizzlingrange">DxgkDdiReleaseSwizzlingRange</a>



<a href="/windows-hardware/drivers/ddi/d3dkmddi/nc-d3dkmddi-dxgkddi_restartfromtimeout">DxgkDdiRestartFromTimeout</a>

