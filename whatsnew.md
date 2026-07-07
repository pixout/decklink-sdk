# Blackmagic Design DeckLink SDK 16.0

Please refer to the Blackmagic Design DeckLink SDK documentation for a detailed explanation of the available functionality.

---

## Changes in Blackmagic DeckLink SDK 16.0

### New Interfaces

#### IDeckLinkStatistics
- Interface allowing query of statistics associated with the DeckLink device.

### Updated Interfaces

#### IDeckLinkVideoBuffer
- **Added:** `GetSize`
  - Provides the size of the buffer.

#### IDeckLinkStatus
- **Added:** `GetInterface`
  - Provides status as an interface.
  - The following status items can return either `BMDDisplayMode` as an integer or `IDeckLinkDisplayMode` as an interface:
    - `bmdDeckLinkStatusDetectedVideoInputMode`
    - `bmdDeckLinkStatusCurrentVideoInputMode`
    - `bmdDeckLinkStatusCurrentVideoOutputMode`
    - `bmdDeckLinkStatusHDMIOutputActualMode`
- **Added:** `GetFlagWithParam`
- **Added:** `GetIntWithParam`
- **Added:** `GetFloatWithParam`
- **Added:** `GetStringWithParam`
- **Added:** `GetBytesWithParam`
  - Provides parameterizable status values.

#### IDeckLinkConfiguration
- **Added:** `SetFlagWithParam`
- **Added:** `GetFlagWithParam`
- **Added:** `SetIntWithParam`
- **Added:** `GetIntWithParam`
- **Added:** `SetFloatWithParam`
- **Added:** `GetFloatWithParam`
- **Added:** `SetStringWithParam`
- **Added:** `GetStringWithParam`
  - Provides parameterizable configuration values.

#### IDeckLinkProfileAttributes
- **Added:** `GetStringWithParam`
  - Provides a parameterizable attribute string.

#### IDeckLinkOutput
- **Deprecated:** `CreateAncillaryData`
  - Use `IDeckLinkVideoFrameAncillaryPackets` instead.

#### IDeckLinkVideoFrame
- **Deprecated:** `GetAncillaryData`
  - Use `IDeckLinkVideoFrameAncillaryPackets` instead.

#### IDeckLinkMutableVideoFrame
- **Deprecated:** `SetAncillaryData`
  - Use `IDeckLinkVideoFrameAncillaryPackets` instead.

### New Types

#### BMDEthernetNMOSRegistryState
- Enumerates the NMOS registry connection state.

#### BMDDeckLinkStatisticID
- Enumerates the set of statistics which may be queried using `IDeckLinkStatistics`.

### Updated Types

#### BMDDeckLinkFrameMetadataID
- **Added:** `bmdDeckLinkFrameMetadataRTPTimestamp`
  - Integer to obtain the RTP timestamp for the captured frame.

#### BMDSupportedVideoModeFlags
- **Added:** `bmdSupportedVideoModeEthernetIP10`
  - Used to check whether the video mode is supported with the IP10 codec.

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigEthernetVideoOutputIP10`
  - Flag to output compressed video with IP10 codec or uncompressed, for video modes that support IP10.
- **Added:** `bmdDeckLinkConfigEthernetUseManualNMOSRegistry`
  - Flag to enable manual setting of NMOS registry address, otherwise the NMOS registry will be found via mDNS discovery.
- **Added:** `bmdDeckLinkConfigEthernetNMOSRegistryAddress`
  - String to set the manual NMOS registry address when enabled.
- **Added:** `bmdDeckLinkConfigParamEthernetUseDHCP`
- **Added:** `bmdDeckLinkConfigParamEthernetStaticLocalIPAddress`
- **Added:** `bmdDeckLinkConfigParamEthernetStaticSubnetMask`
- **Added:** `bmdDeckLinkConfigParamEthernetStaticGatewayIPAddress`
- **Added:** `bmdDeckLinkConfigParamEthernetStaticPrimaryDNS`
- **Added:** `bmdDeckLinkConfigParamEthernetStaticSecondaryDNS`
- **Added:** `bmdDeckLinkConfigParamEthernetVideoOutputAddress`
- **Added:** `bmdDeckLinkConfigParamEthernetAudioOutputAddress`
- **Added:** `bmdDeckLinkConfigParamEthernetAncillaryOutputAddress`
  - Network configuration items for a specific Ethernet interface.
- **Removed:** `bmdDeckLinkConfigEthernetUseDHCP`
- **Removed:** `bmdDeckLinkConfigEthernetStaticLocalIPAddress`
- **Removed:** `bmdDeckLinkConfigEthernetStaticSubnetMask`
- **Removed:** `bmdDeckLinkConfigEthernetStaticGatewayIPAddress`
- **Removed:** `bmdDeckLinkConfigEthernetStaticPrimaryDNS`
- **Removed:** `bmdDeckLinkConfigEthernetStaticSecondaryDNS`
- **Removed:** `bmdDeckLinkConfigEthernetVideoOutputAddress`
- **Removed:** `bmdDeckLinkConfigEthernetAudioOutputAddress`
- **Removed:** `bmdDeckLinkConfigEthernetAncillaryOutputAddress`
  - Use the configuration items for the specific Ethernet interface instead.

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkNumberOfEthernetConnectors`
  - Integer to specify the number of Ethernet connectors for the device.
- **Added:** `BMDDeckLinkParamEthernetMACAddress`
  - Local MAC address string for the specific Ethernet interface.
- **Removed:** `BMDDeckLinkEthernetMACAddress`
  - Use the attribute item for the specific Ethernet interface instead.

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusEthernetManualNMOSRegistry`
  - Current manual NMOS registry state.
- **Added:** `bmdDeckLinkStatusEthernetCurrentNMOSRegistry`
  - Address of the current NMOS registry.
- **Added:** `bmdDeckLinkStatusAncillaryInputSignalLocked`
  - True if the ancillary input signal is locked.
- **Added:** `bmdDeckLinkStatusParamEthernetSFPStaticInfo`
  - The static information of the connected SFP module for the specific Ethernet interface.
- **Added:** `bmdDeckLinkStatusParamEthernetLink`
  - Current link state for the specific Ethernet interface.
- **Added:** `bmdDeckLinkStatusParamEthernetLinkMbps`
  - Current link speed for the specific Ethernet interface.
- **Added:** `bmdDeckLinkStatusParamEthernetLocalIPAddress`
- **Added:** `bmdDeckLinkStatusParamEthernetSubnetMask`
- **Added:** `bmdDeckLinkStatusParamEthernetGatewayIPAddress`
- **Added:** `bmdDeckLinkStatusParamEthernetPrimaryDNS`
- **Added:** `bmdDeckLinkStatusParamEthernetSecondaryDNS`
  - The current negotiated or static network addresses for the specific Ethernet interface.
- **Added:** `bmdDeckLinkStatusParamEthernetVideoOutputAddress`
- **Added:** `bmdDeckLinkStatusParamEthernetAudioOutputAddress`
- **Added:** `bmdDeckLinkStatusParamEthernetAncillaryOutputAddress`
  - The current multicast addresses for Video/Audio/Ancillary streams for the specific Ethernet interface.
- **Removed:** `bmdDeckLinkStatusEthernetLink`
- **Removed:** `bmdDeckLinkStatusEthernetLinkMbps`
- **Removed:** `bmdDeckLinkStatusEthernetLocalIPAddress`
- **Removed:** `bmdDeckLinkStatusEthernetSubnetMask`
- **Removed:** `bmdDeckLinkStatusEthernetGatewayIPAddress`
- **Removed:** `bmdDeckLinkStatusEthernetPrimaryDNS`
- **Removed:** `bmdDeckLinkStatusEthernetSecondaryDNS`
- **Removed:** `bmdDeckLinkStatusEthernetVideoOutputAddress`
- **Removed:** `bmdDeckLinkStatusEthernetAudioOutputAddress`
- **Removed:** `bmdDeckLinkStatusEthernetAncillaryOutputAddress`
  - Use the status items for the specific Ethernet interface instead.

### New Samples

#### KeyerOutput
- Cross platform sample to demonstrate keyer interface. Replaces Windows GdiKeyer and Mac DeckLinkKeyer samples.

#### MultiPreview
- Replaces QuadPreview, adding command-line argument to select preview grid size.

### Updated Samples

- Samples implementing the `IDeckLinkVideoBuffer` interface have been updated to add the `GetSize` method.

#### DeviceConfigure
- Add support for setting multicast output addresses.
- Add support for setting Ethernet IP addresses with parameterizable interface number.

#### DeviceList
- Display Ethernet MAC addresses with parameterizable interface number.

#### DeviceStatus
- Add Ethernet status tab with selectable parameterizable interface number.

#### InputLoopThrough
- Add command-line arguments to select devices, bypass genlock reference and inject processing delay.

### Updated Examples

#### AncillaryCapture
- Add command-line argument to select target device.

#### AncillaryOutput
- Add command-line argument to select target device.

#### StatusMonitor
- Add support to display Ethernet status items with parameterizable interface number.
- Add support for Ethernet statistics with command-line argument to set poll rate.

---

## Changes in Blackmagic DeckLink SDK 15.2

### Updated Types

#### BMDVideoConnection
- **Added:** `bmdVideoConnectionInternal`
  - New entry for products supporting an internal connection.

---

## Changes in Blackmagic DeckLink SDK 15.0

### New Types

#### BMDAudioOutputXLRDelayType
- Enumerates the audio output XLR delay unit type.

#### BMDLanguage
- Enumerates a list of supported languages.

#### BMDAudioMeterType
- Enumerates the types of audio meters.

### Updated Types

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigAudioMeterType`
  - Integer to configure the front-panel audio meter type.
- **Added:** `bmdDeckLinkConfigAnalogAudioOutputChannelsMutedByHeadphone`
- **Added:** `bmdDeckLinkConfigAnalogAudioOutputChannelsMutedBySpeaker`
  - Flags to mute audio outputs when using headphones or speaker.
- **Added:** `bmdDeckLinkConfigExtendedDesktop`
  - Flag to enable extended desktop on a supported device.
- **Added:** `bmdDeckLinkConfigAudioOutputXLRDelayTime`
- **Added:** `bmdDeckLinkConfigAudioOutputXLRDelayFrames`
- **Added:** `bmdDeckLinkConfigAudioOutputXLRDelayType`
  - Integers to configure the audio output XLR delay relative to video.
- **Added:** `bmdDeckLinkConfigSpeakerVolume`
  - Floating point to set the speaker value.
- **Added:** `bmdDeckLinkConfigDisplayLanguage`
  - Integer to configure the front-panel display language.

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkSupportsExtendedDesktop`
  - Flag to specify whether extended desktop is supported by the device.
- **Added:** `BMDDeckLinkXLRDelayMsMaximum`
- **Added:** `BMDDeckLinkXLRDelayFramesMaximum`
  - Integer values to specify maximum audio output XLR delays for each unit type.

### New Samples

#### LoopThroughWithMetalCompositing
- Demonstrates efficient transfers and conversions between Metal render encoder and DeckLink capture and playback.

---

## Changes in Blackmagic DeckLink SDK 14.4

### New Interfaces

#### IDeckLinkIPFlowAttributes
- Provides methods to query attributes associated with a DeckLink IP flow.

#### IDeckLinkIPFlowStatus
- Provides methods to query the status information associated with a DeckLink IP flow.

#### IDeckLinkIPFlowSetting
- Provides methods to query and modify the settings associated with a DeckLink IP flow.

#### IDeckLinkIPFlow
- The base interface representing a SMPTE 2110 IP flow.

#### IDeckLinkIPFlowIterator
- Provides an iterator to enumerate the `IDeckLinkIPFlow` objects associated with a DeckLink IP device.

#### IDeckLinkIPExtensions
- Provides access to the individual IP flows or iterator associated with a DeckLink IP device.

### New Types

#### BMDIPFlowDirection
- Enumerates the direction of the IP flow.

#### BMDIPFlowType
- Enumerates the type of the IP flow.

#### BMDDeckLinkIPFlowAttributeID
- Enumerates the attribute items associated with an IP flow.

#### BMDDeckLinkIPFlowStatusID
- Enumerates the status items associated with an IP flow.

#### BMDDeckLinkIPFlowSettingID
- Enumerates the setting items associated with an IP flow.

#### BMDIPFlowID
- Integer type that can be used to identify an IP flow.

### Updated Types

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigEthernetPTPLogAnnounceInterval`
  - Configuration item for setting the PTP log announce interval value.

#### BMDNotifications
- **Added:** `bmdIPFlowStatusChanged`
  - Notification value for when an IP flow status item has changed.
- **Added:** `bmdIPFlowSettingChanged`
  - Notification value for when an IP flow setting item has changed.

### Updated Samples

#### DeviceConfigure
- Add support for setting PTP log announce interval.

### New Examples

#### DeckLinkIPExample
- Provides example for connecting IP flows.

---

## Changes in Blackmagic DeckLink SDK 14.3

### New Interfaces

#### IDeckLinkVideoBuffer
- Provides access to the underlying buffer of an `IDeckLinkVideoFrame` object.

#### IDeckLinkVideoBufferAllocator
- A user implemented class for providing custom `IDeckLinkVideoBuffer` objects when requested by the DeckLink API during capture.

#### IDeckLinkVideoBufferAllocatorProvider
- A user implemented callback class to provide custom `IDeckLinkVideoBufferAllocator` objects when capture is enabled.

#### IDeckLinkMacOutput
- A macOS specific extension to the `IDeckLinkOutput` interface, providing convenience for creating output frames directly from CVPixelBuffer objects.

#### IDeckLinkMacVideoBuffer
- Provides macOS and CVPixelBuffer specific operations supplementary to the `IDeckLinkVideoBuffer` interface.

#### IDeckLinkVideoFrameMutableMetadataExtensions
- Allows setting frame metadata associated with a video frame.

### Updated Interfaces

#### IDeckLinkOutput
- **Added:** `CreateVideoFrameWithBuffer` method allowing new frame creation with a custom buffer.
- **Added:** `RowBytesForPixelFormat` method for determining the frame row bytes from the pixel format and frame width.
- **Removed:** `SetVideoOutputFrameMemoryAllocator` method. A custom buffer can be provided when creating the video frame with the `CreateVideoFrameWithBuffer` method.

#### IDeckLinkInput
- **Added:** `EnableVideoInputWithAllocatorProvider` method to optionally enable input with custom buffer allocators.
- **Removed:** `SetVideoInputFrameMemoryAllocator` method. Providing custom allocators for input is set with the `EnableVideoInputWithAllocators` method.

#### IDeckLinkEncoderInput
- **Removed:** `SetMemoryAllocator` method. Captured H.265 packets will be provided with the default memory allocator.

#### IDeckLinkVideoFrame
- **Removed:** `GetBytes` method. Buffer access is provided by the `IDeckLinkVideoBuffer` interface.

#### IDeckLinkMutableVideoFrame
- **Added:** `SetInterfaceProvider` method to set a provider that allows querying another interface from the video frame.

#### IDeckLinkVideoConversion
- **Added:** `ConvertNewFrame` method to convert a source frame directly into a new frame, optionally with a custom video buffer.

### Deprecated Interfaces

#### IDeckLinkMemoryAllocator
- For setting custom input memory allocators, implement the `IDeckLinkVideoBufferAllocatorProvider` and `IDeckLinkVideoBufferAllocator` interfaces instead.

### New Types

#### BMDBufferAccessFlags
- Enumerates the buffer access requirements for an `IDeckLinkVideoBuffer` object.

### Updated Samples

- Samples requiring pixel buffer access have been updated with the `IDeckLinkVideoBuffer` interface.
- Samples with output have been updated use the `IDeckLinkOutput::RowBytesForPixelFormat` method to determine frame row bytes.

#### CaptureStills / StillsCSharp
- The video frame conversion to BGRA pixel format is performed with `IDeckLinkVideoConversion::ConvertNewFrame`.

#### SignalGenHDR
- HDR metadata is set with the `IDeckLinkVideoFrameMutableMetadataExtensions` interface.

#### SignalGenerator / TestPattern
- 3D extensions are now associated with the output video frame with `IDeckLinkMutableVideoFrame::SetInterfaceProvider`.

#### FileCapture / FilePlayback
- The macOS samples add support for HEVC with colorspace and HDR metadata.
- The underlying video frames in the macOS samples are backed by CVPixelBuffer.
- The Windows samples are updated with new buffer and allocator interfaces.

#### MetalOutput
- Add support for output conversion to YUV with tile or compute shader.
- Output frames are generated directly from the IOSurface backed Metal textures.

#### StillsCSharp
- Updates with new buffer interface to manage video frames backed by Bitmap data.

---

## Changes in Blackmagic DeckLink SDK 14.2

### Updated Types

#### BMDVideoOutputFlags
- **Added:** `bmdVideoOutputDolbyVision`
  - Flag to enable Dolby Vision on HDMI output.

#### BMDSupportedVideoModeFlags
- **Added:** `bmdSupportedVideoModeDolbyVision`
  - Used to check whether the video mode is supported with Dolby Vision.

#### BMDFrameFlags
- **Added:** `bmdFrameContainsDolbyVisionMetadata`
  - Flag to specify that the frame contains Dolby Vision metadata.

#### BMDColorspace
- **Added:** `bmdColorspaceDolbyVisionNative`
  - Colorspace for native Dolby Vision, intended as destination colorspace for output conversion.
- **Added:** `bmdColorspaceP3D65`
  - P3 colorspace with D65 white point, must be converted to output Dolby Vision.
- **Added:** `bmdColorspaceUnknown`
  - Unspecified colorspace for disabling output colorspace conversion.

#### BMDDeckLinkFrameMetadataID
- **Added:** `bmdDeckLinkFrameMetadataDolbyVision`
  - Used to query the application for the Dolby Vision metadata buffer associated with a video frame.

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigOutputValidateEDIDForDolbyVision`
  - Configuration flag to disable validation of sink EDID for Dolby Vision.
- **Added:** `bmdDeckLinkConfigVideoOutputConversionColorspaceSource`
- **Added:** `bmdDeckLinkConfigVideoOutputConversionColorspaceDestination`
  - Used to specify source and destination colorspaces for the output colorspace conversion.
- **Added:** `bmdDeckLinkConfigDolbyVisionCMVersion`
  - Used to configure the Dolby Vision content mapping version for output.
- **Added:** `bmdDeckLinkConfigDolbyVisionMasterMinimumNits`
- **Added:** `bmdDeckLinkConfigDolbyVisionMasterMaximumNits`
  - Used to configure the Dolby Vision mastering monitor minimum and maximum brightness.

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusSinkSupportsDolbyVision`
  - The Dolby Vision content mapping version of the connected sink.

---

## Changes in Blackmagic DeckLink SDK 14.1

### New Types

#### BMDFormatFlags
- Enumerates the possible format flags for the output HDMI pixel format.

### Updated Types

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusHDMIOutputActualMode`
  - The actual HDMI output display mode.
- **Added:** `bmdDeckLinkStatusHDMIOutputActualFormatFlags`
  - The format flags for the actual HDMI output.
- **Added:** `bmdDeckLinkStatusHDMIOutputFRLRate`
- **Added:** `bmdDeckLinkStatusHDMIInputFRLRate`
  - The current HDMI FRL line rate.
- **Added:** `bmdDeckLinkStatusHDMIOutputTMDSLineRate`
  - The current TMDS line rate of HDMI output in MHz.

---

## Changes in Blackmagic DeckLink SDK 14.0

### New Types

#### BMDMezzanineType
- Enumerates the mezzanine boards that can be attached to some DeckLink devices.

### Updated Types

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkMaximumHDMIAudioChannels`
  - The maximum number of audio channels embedded on HDMI.
- **Added:** `BMDDeckLinkMezzanineType`
  - The mezzanine board currently attached to the DeckLink device.

---

## Changes in Blackmagic DeckLink SDK 12.9

### Updated Types

#### BMDPixelFormat
- **Added:** `bmdFormat10BitYUVA`
  - New 10-bit YUV format with Alpha component.

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkHasMonitorOut`
  - Flag to determine whether device supports scheduling of monitor output only frames.

#### BMDFrameFlags
- **Added:** `bmdFrameFlagMonitorOutOnly`
  - Frame flag to output only on Monitor Out.

### Updated Samples

#### DeviceList
- Add 10-bit YUVA pixel format.
- Add check for support of Monitor Out only feature.

---

## Changes in Blackmagic DeckLink SDK 12.8

### Updated Types

#### BMDSupportedVideoModeFlags
- **Added:** `bmdSupportedVideoModePsF`
  - Used to check whether PsF interpretation is supported for the video mode.

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusEthernetLinkMbps`
  - Current link speed for devices that support Ethernet.

### Updated Samples

#### DeviceList
- Add support for PsF video modes.
- Add support for keying modes for devices that support Ethernet.

#### DeviceStatus / DeviceStatusCSharp
- Add support for Ethernet link speed.

#### FileCapture / FilePlayback
- Mac samples changed to use persistent ID for device identification.

#### CapturePreview / SignalGenHDR / SignalGenerator / TestPattern
- Linux samples add masking of inactive devices.

### Updated Examples

#### StatusMonitor
- Add support for Ethernet link speed.

#### SynchronizedPlayback
- Add support for DeckLink IP cards and improved support for when all playback devices are on same card.

---

## Changes in Blackmagic DeckLink SDK 12.6

### New Types

#### BMDEthernetLinkState
- Enumerates the Ethernet link state.

### Updated Types

#### BMDVideoConnection
- **Added:** `bmdVideoConnectionEthernet`
- **Added:** `bmdVideoConnectionOpticalEthernet`
  - New entries for devices that support Ethernet connections.

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigEthernetUseDHCP`
  - Flag to enable DHCP, otherwise use static network address.
- **Added:** `bmdDeckLinkConfigEthernetStaticLocalIPAddress`
- **Added:** `bmdDeckLinkConfigEthernetStaticSubnetMask`
- **Added:** `bmdDeckLinkConfigEthernetStaticGatewayIPAddress`
  - Strings to assign local IP addresses when DHCP is disabled.
- **Added:** `bmdDeckLinkConfigEthernetStaticPrimaryDNS`
- **Added:** `bmdDeckLinkConfigEthernetStaticSecondaryDNS`
  - Strings to assign static DNS addresses for devices that support Ethernet.
- **Added:** `bmdDeckLinkConfigEthernetPTPFollowerOnly`
  - Flag to prevent the DeckLink from negotiating to become PTP leader.
- **Added:** `bmdDeckLinkConfigEthernetPTPUseUDPEncapsulation`
  - Flag to enable UDP encapsulation of PTP, otherwise Ethernet encapsulation is used.
- **Added:** `bmdDeckLinkConfigEthernetPTPPriority1`
- **Added:** `bmdDeckLinkConfigEthernetPTPPriority2`
  - Integers to set the PTP clock election priority and secondary priority.
- **Added:** `bmdDeckLinkConfigEthernetPTPDomain`
  - Integer to set the domain to group PTP devices.
- **Added:** `bmdDeckLinkConfigReferenceOutputMode`
  - Sets the video mode (`BMDDisplayMode`) for devices that support a configurable reference output.
- **Added:** `bmdDeckLinkConfigEthernetVideoOutputAddress`
- **Added:** `bmdDeckLinkConfigEthernetAudioOutputAddress`
- **Added:** `bmdDeckLinkConfigEthernetAncillaryOutputAddress`
  - Strings to set the multicast addresses for Video/Audio/Ancillary streams.
- **Added:** `bmdDeckLinkConfigEthernetAudioOutputChannelOrder`
  - String to set output audio channel order in the transmitted SDP.

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkEthernetMACAddress`
  - Local MAC address string for devices that support Ethernet.

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusEthernetLink`
  - Current link state for devices that support Ethernet.
- **Added:** `bmdDeckLinkStatusEthernetLocalIPAddress`
- **Added:** `bmdDeckLinkStatusEthernetSubnetMask`
- **Added:** `bmdDeckLinkStatusEthernetGatewayIPAddress`
  - The current negotiated or static local IP addresses for devices that support Ethernet.
- **Added:** `bmdDeckLinkStatusEthernetPrimaryDNS`
- **Added:** `bmdDeckLinkStatusEthernetSecondaryDNS`
  - The current static or negotiated DNS addresses for devices that support Ethernet.
- **Added:** `bmdDeckLinkStatusEthernetPTPGrandmasterIdentity`
  - The current negotiated PTP grandmaster clock identity for devices that support Ethernet.
- **Added:** `bmdDeckLinkStatusEthernetVideoOutputAddress`
- **Added:** `bmdDeckLinkStatusEthernetAudioOutputAddress`
- **Added:** `bmdDeckLinkStatusEthernetAncillaryOutputAddress`
  - The current multicast addresses for Video/Audio/Ancillary streams.
- **Added:** `bmdDeckLinkStatusEthernetAudioInputChannelOrder`
  - The input audio channel order in the received SDP.

### New Samples

#### MetalOutput
- Provides example of outputting video frames generated by IOSurface-backed Metal textures.

### Updated Samples

#### DeviceStatus / DeviceStatusCSharp
- Add Ethernet link, IP addresses, DNS addresses, PTP grandmaster identity, multicast addresses and audio channel order status items.

#### CapturePreview / CapturePreviewCSharp / FileCapture / QuadCapture
- Add support for Ethernet connections.

#### DeviceConfigure
- Add support for Ethernet connections.
- Add support to assign Ethernet PTP configuration items.

#### DeviceList
- Add support for Ethernet connections.
- Add support local Ethernet MAC address.

#### CapturePreview / SignalGenerator
- Mac samples refreshed with com_ptr wrapper.

### Deprecated Samples

#### BypassControl

#### OpenGLOutput
- Mac sample replaced with MetalOutput sample.

### Updated Examples

#### StatusMonitor
- Add Ethernet link, IP addresses, DNS addresses, PTP grandmaster identity, multicast addresses and audio channel order status items.
- Add command line option to select target device.

---

## Changes in Blackmagic DeckLink SDK 12.4

### Updated Samples

#### All Linux samples
- Added support for aarch64.
- 32-bit x86 binaries removed.

---

## Changes in Blackmagic DeckLink SDK 12.3

- On Mac, the `IDeckLinkCocoaScreenPreviewCallback` interface has been updated to render with Metal.
- On Windows and Linux, the `IDeckLinkGLScreenPreviewHelper` interface adds support for OpenGL 3.2 rendering.

### New Interfaces

#### IDeckLinkMetalScreenPreviewHelper
- New helper for Mac providing Metal-based screen preview rendering.

#### IDeckLinkWPFDX9ScreenPreviewHelper
- New helper for Windows WPF applications providing DirectX based preview rendering.

### New Functions

#### CreateOpenGL3ScreenPreviewHelper
- Called to create `IDeckLinkGLScreenPreviewHelper` interface with OpenGL 3.2 rendering.

#### CreateMetalScreenPreviewHelper
- Called to create `IDeckLinkMetalScreenPreviewHelper` interface.

### Updated Samples

#### CapturePreview / SignalGenerator / SignalGenHDR
- Win and Linux samples updated to use OpenGL 3.2 screen preview helper.

#### QuadPreview
- Mac sample updated to use `IDeckLinkMetalScreenPreviewHelper`.
- Win and Linux samples updated to use OpenGL 3.2 screen preview helper.

#### CapturePreviewCSharp / SignalGenCSharp
- Samples are updated to WPF and use `IDeckLinkWPFDX9ScreenPreviewHelper`.

#### SignalGenerator
- Mac sample now uses App Sandbox entitlement.

#### ClosedCaptions
- Sample sets svc_info_start flag in CDP header.

---

## Changes in Blackmagic DeckLink SDK 12.2.2

### Updated Samples

#### InputLoopThrough
- Change monotonic clock reference in Linux.

---

## Changes in Blackmagic DeckLink SDK 12.2

### Updated Samples

#### InputLoopThrough
- Changed latency calculations to use common system clock.

---

## Changes in Blackmagic DeckLink SDK 12.1

### Updated Types

#### BMDReferenceStatus
- **Added:** `bmdReferenceUnlocked`
  - New item for where genlock reference lock has not be achieved.

### Updated Samples

#### DeviceStatusCSharp
- Improve application stability when reading `bmdDeckLinkStatusReceivedEDID` status item.

#### H265TestEncoder
- Mac sample improves support for Retina displays.

#### LoopThroughWithOpenGLCompositing / LoopThroughWithDX11Compositing
- Samples updated to NVIDIA GPUDirect v1.70 libraries.

#### SignalGenerator
- Ensure old timecode is cleared when rescheduling completed frames.
- Fix misalignment of RP188 VITC timecode on pip/dropout frame.

### Updated Examples

#### RP188VitcTimecode
- Ensure old timecode is cleared when rescheduling completed frames.

---

## Changes in Blackmagic DeckLink SDK 12.0

### Updated Samples

#### All Mac Samples
- Projects have been updated to build Universal binaries to run on both Apple M1 and Intel processors.

#### SignalGenerator / SignalGenHDR
- Modified Mac sample to exit when closing the application window.

#### DeviceStatus
- Fixed formatting of bmdDeckLinkStatusReceivedEDID status item.

### Updated Examples

#### All Mac Examples
- Project is updated to build Universal binaries to run on both Apple M1 and Intel processors.

#### StatusMonitor
- No longer reports unknown status IDs as they should be ignored.
- Improved formatting of specific status items.

#### VancCapture
- Added support for multiple Ancillary Data packets per line.

---

## Changes in Blackmagic DeckLink SDK 11.7

### Updated Examples

#### AutomaticModeDetection
- `IDeckLinkInputCallback::VideoInputFormatChanged` callback is modified to enable input with a pixel format matching the format detected with `BMDDetectedVideoInputFormatFlags` flags.

---

## Changes in Blackmagic DeckLink SDK 11.6

### Updated Types

#### BMDDeckLinkStatusID
- **Added:** `bmdDeckLinkStatusDetectedVideoInputFormatFlags`
  - New status item of the video input flags when auto-mode detection is enabled.
- **Added:** `bmdDeckLinkStatusDetectedVideoInputFieldDominance`
  - New status item of the detected field dominance of the input video signal.
- **Added:** `bmdDeckLinkStatusDetectedVideoInputColorspace`
  - New status item of the detected colorspace of the input video signal.
- **Added:** `bmdDeckLinkStatusDetectedVideoInputDynamicRange`
  - New status item of the detected dynamic range of the input video signal.
- **Added:** `bmdDeckLinkStatusDetectedSDILinkConfiguration`
  - New status item of the detected SDI link configuration of the input video signal.
- **Removed:** `bmdDeckLinkStatusDetectedVideoInputFlags`
  - Status item is replaced by `bmdDeckLinkStatusDetectedVideoInputFormatFlags`.

#### BMDDetectedVideoInputFormatFlags
- **Added:** `bmdDetectedVideoInput12BitDepth`
- **Added:** `bmdDetectedVideoInput10BitDepth`
- **Added:** `bmdDetectedVideoInput8BitDepth`
  - Flags to determine the detected color-depth of the video input signal.

#### BMDVideoInputFormatChangedEvents
- **Modified:** `bmdVideoInputDisplayModeChanged` - added change to detected video input dual stream 3D to event (`bmdDetectedVideoInputDualStream3D`)
- **Modified:** `bmdVideoInputColorspaceChanged`
  - Added change to detected video input color bit depth to event
  - Removed change to detected video input dual stream 3D from event

### Updated Examples

#### StatusMonitor
- Updated to support new `BMDDeckLinkStatusID` items.

### New Samples

#### DeviceStatus
- Cross-platform sample to monitor the status items for the selected device.

#### DeviceStatusCSharp
- C# WPF sample to monitor the status items for the selected device.

### Updated Samples

#### CapturePreview / CaptureStills / QuadPreview
- `IDeckLinkInputCallback::VideoInputFormatChanged` callback is modified to enable input with a pixel format matching the format detected with new `BMDDetectedVideoInputFormatFlags` flags.

#### Capture / FileCapture
- `IDeckLinkInputCallback::VideoInputFormatChanged` callback behavior is modified to check new `BMDDetectedVideoInputFormatFlags` flags for colorspace change.

---

## Changes in Blackmagic DeckLink SDK 11.5.1

### New Types

#### BMDInternalKeyingAncillaryDataSource
- Enumerates the source for VANC and timecode data when performing internal keying.

### Updated Types

#### BMDDeckLinkConfigurationID
- **Added:** `bmdDeckLinkConfigInternalKeyingAncillaryDataSource`
  - Provides ability to set source for VANC and timecode data when performing internal keying.

#### BMDDisplayMode
- **Removed:** `bmdModeCintelRAW`
- **Removed:** `bmdModeCintelCompressedRAW`

#### BMDPixelFormat
- **Removed:** `bmdFormat12BitRAWGRBG`
- **Removed:** `bmdFormat12BitRAWJPEG`

#### BMDFrameFlags
- **Removed:** `bmdFrameContainsCintelMetadata`

#### BMDDeckLinkFrameMetadataID
- **Removed:** Multiple Cintel-related metadata items (see original document for complete list)

### New Examples

#### VancCapture
- Demonstrates extraction of SMPTE ST 291 Type 2 ANC data from incoming video frame.

### Updated Samples

#### DeviceList
- Added displaying of HDMI timecode support for devices.

#### CaptureStills
- Improved reference counting of interfaces.

#### Capture
- Added support for 8-bit YUV capture.

#### CapturePreview
- Migrated Linux sample to Qt5. Added support for com_ptr wrapper.
- Improved Windows sample with CComPtr and masking of inactive devices from input device combobox. Add support for resizable dialog.
- Modified Mac sample to mask inactive devices from input device popup.

#### SignalGenHDR
- Migrated Linux sample to Qt5.

#### SignalGenerator
- Migrated Linux sample to Qt5. Added support for com_ptr wrapper.
- Improved Windows sample with CComPtr and masking of inactive devices from output device combobox. Add support for resizable dialog.
- Modified Mac sample to mask inactive devices from output device popup.
- Win/Mac samples add support for timecode output.

---

## Changes in Blackmagic DeckLink SDK 11.5

### Updated Interfaces

#### IDeckLinkOutput
- The `DoesSupportVideoMode` method parameter list has been modified to check support with output conversion.

#### IDeckLinkInput
- The `DoesSupportVideoMode` method parameter list has been modified to check support with input conversion.

### Updated Types

#### BMDDeckLinkAttributeID
- **Added:** `BMDDeckLinkMinimumPrerollFrames`
  - Integer that specifies the minimum number of preroll frames required for scheduled playback on an output device.
- **Added:** `BMDDeckLinkSupportedDynamicRange`
  - Attribute that specifies which HDR transfer functions are supported by the device.

### Updated Samples

#### DeviceList
- Modified with command-line arguments to print display modes per connection and display modes per conversion.

#### InputLoopThrough
- The existing Mac/Windows samples have been replaced by cross-platform command-line loop though with latency measurements.

#### SignalGenHDR
- Use Rec.2020 chromaticity coordinates for default values.
- (Linux) Fixed issue when changing selected output device.

#### QuadPreview
- Improved message handling on device disconnects.

#### SignalGenerator / SignalGenHDR / TestPattern
- SDI output is configured either 422 or 444 colorspace, to match the selected pixel format.

---

## Changes in Blackmagic DeckLink SDK 11.4

### Updated Interfaces

#### IDeckLinkOutput
- The base time for `GetHardwareReferenceClock` hardware reference time output has changed for consistency with `GetFrameCompletionReferenceTimestamp` method.

### Updated Samples

#### FilePlayback
- Added support for 2K/4K DCI modes.
- (Mac) Added YUV conversion where requested output display mode does not support RGB format.
- (Win) Enabled hardware acceleration for source reader (Win8/10).

#### QuadPreview
- Fixed DeckLink reference count issue preventing device notifications on repeated Thunderbolt connect/disconnects.

### Updated Examples

#### StatusMonitor
- Modified display mode reporting to use `IDeckLinkDisplayMode::GetName` method.

### Deprecated Samples

#### DeckControl
- Refer to CaptureFromTape and ExportToTape samples for correct usage of `IDeckLinkDeckControl` interface.

---

*For earlier SDK versions (11.3 and below), please refer to the original document.*

---

## Copyright and Trademarks

Some applications may use third party code under license. For details, please refer to the included "Third Party Licenses.rtf" document.

Copyright 2025 Blackmagic Design. All rights reserved. 'Blackmagic Design', 'Blackmagic', 'Blackmagic Cloud', 'DaVinci Resolve', 'Fusion', 'Fairlight', 'Ultimatte', 'URSA', 'PYXIS', 'HyperDeck', 'DeckLink', 'HDLink', 'Videohub', 'Intensity' and 'Leading the creative video revolution' are registered trademarks in the US and other countries. All other company and product names may be trademarks of their respective companies with which they are associated. Thunderbolt and the Thunderbolt logo are trademarks of Intel Corporation in the U.S. and/or other countries. Dolby, Dolby Vision, and the double-D symbol are registered trademarks of Dolby Laboratories Licensing Corporation.

**Updated October 24, 2025**