---
author: joshbax-msft
title: Test.InputResolution
description: Test.InputResolution
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: b8d4ec65-3b61-43ff-904e-bf445a5a414c
---

# Test.InputResolution


This test verifies the device resolution by ensuring that it can support what it reports. Between two slow swipes, every logical unit of X should be hit, and every value of Y when moving down and up vertically.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Input.PrecisionTouchpad.Precision.InputResolution System.Client.PrecisionTouchpad.PrecisionTouchpad</p>
<p>[See the system hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254482)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~2 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Manual</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Mouse or other Pointing Device Testing Prerequisites](mouse-or-other-pointing-device-testing-prerequisites.md).

1.  Drag one precision contact across the touchpad at 1-2mm/second from left to right, and again from right to left. (This can be done anywhere in the middle 80% of the touchpad surface.)

    All Y-axis movement or jitter is ignored in this test when measuring X values (and vice-versa), so if the PT3 cannot move smoothly at a slow pace, a precision contact can be moved by hand across the touchpad to avoid extra friction.

2.  Repeat vertically, dragging first from top to bottom, then from bottom to top.

**Note**  
If all logical x/y coordinates are hit after one swipe on that axis, the test automatically passes without a swipe in the other direction. This is expected.

 

## Troubleshooting


For troubleshooting information, see [Troubleshooting Device.Input Testing](troubleshooting-deviceinput-testing.md).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error</th>
<th>Description/Workaround</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>[20] positional delta too large</p></td>
<td><p>There was a jump in X coordinates between 2 packets.</p>
<p>To investigate, open the Hid log in Excel, add a column for DeltaX, and populate it with the differences between the X’s. You can then filter out 0s (packets in which the contact has not yet moved horizontally), and expected 1s.</p></td>
</tr>
<tr class="even">
<td><p>[35] logical coordinate not found</p></td>
<td><p>Either the minimum or maximum value was never hit in the two passes. The number given is the X or Y value which was not hit (depending on whether the iteration is for horizontal or vertical drags, respectively).</p></td>
</tr>
<tr class="odd">
<td><p>[31] Too low percent of logical coordinates found</p></td>
<td><p>Less than 80% of the logical coordinates were reported during the duration of the test.</p></td>
</tr>
</tbody>
</table>

 

## More information


### Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ptlogo.exe Test.InputResolution.json</strong></p></td>
<td><p>Runs the test.</p></td>
</tr>
</tbody>
</table>

 

### File list

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>File</th>
<th>Location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ptlogo.exe</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\input\PrecisionTouchpad\</p></td>
</tr>
<tr class="even">
<td><p>config.json</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\input\PrecisionTouchpad\</p></td>
</tr>
<tr class="odd">
<td><p>Test.InputResolution.json</p></td>
<td><p><em>&lt;testbinroot&gt;</em>\input\PrecisionTouchpad\</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Test.InputResolution%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



