# Siemens v2.2 HBCD Protocol Release Notes

## Installation Instructions

For HBCD sites, please make sure to follow the HBCD protocol upgrade SOP which will help ensure there are records of when each protocol update is applied at your site.

Before importing the HBCD protocol, please ensure you have received and installed the necessary C2P sequence packages for access to the latest versions of each sequence:

- **[Multiband EPI (University of Minnesota) Sequence Download and Installation Instructions](https://www.cmrr.umn.edu/multiband/)**

- **[vNav Morphometry (University of Pennsylvania) Instructions](https://mri-motion-correction-vnav-morphometry.readthedocs-hosted.com/en/nxva30a_162141/requesting.html)**

- **QALAS (Boston Children’s Hospital):** Please contact Borjan Gagoski (Borjan.Gagoski@childrens.harvard.edu)

- **ISTHMUS spectroscopy (Johns Hopkins University):** Please contact Richard Edden (edden@jhu.edu)

Without these C2P packages installed, the protocol cannot be imported.

**IMPORTANT DIRECTIONS BEFORE SEQUENCE INSTALLATION:** Siemens has identified a bug in NXVA30A SP02 (the software baseline used for this study) that may cause your scanner to become non-responsive during the installation of the certificates required for custom sequences. Please ensure you have SP02 SD05 installed on your scanner before proceeding, as this fixes the bug and allows you to install custom sequences.

**IMPORTANT UPGRADE NOTE FOR v2.2** The HBCD vNav Structural sequence package from University of Pennsylvania has been updated since the HBCD v2.1 protocol. To enable full compatibility with the FIRMM tablet, please install the latest version of the HBCD vNav Structural sequence package on your scanner. The latest version can be requested from Dylan Tisdall (mtisdall@pennmedicine.upenn.edu)



**N4VE11C (a.k.a., VE11C) systems**

This software baseline is no longer supported. All scanners must upgrade to NXVA30A SP02 to run the v2.0 or later protocol.

**NXVA30A (a.k.a., XA30) systems**



1. This package can only be installed on systems with the SP02 service pack installed. To confirm this is installed, go to the "?" menu in the top-right corner of the scanner console, then select "About", then click on “System Info”; a window should pop up with the following version information:

    Numaris/X VA30A-03GR<br>
    syngo OAK_v7QR2201


    or


    Numaris/X VA30A-03MV<br>
    syngo OAK_v7QR2301B


    If you double click the "VA30A-03GR" (or “VA30A-03MV”), it shows the build stamp, which should be


    Numaris/X VA30A.Night_20220414.2 C228547


    or


    Numaris/X VA30A.Night_20230910.1 C338286


    If your version and/or build stamp do not match these values, please contact Siemens to upgrade to the SP02 or SP03 service pack.

2. Note that this protocol requires the CS_SPACE, SMS, and SVS licenses from Siemens be activated on your scanner. If you do not have these licenses, protocols will not import or run correctly. HBCD has negotiated group pricing for the CS_SPACE and SVS licenses if you do not already have them activated.
3. Please put the files “DiffusionVectors_HBCD_pe1_03142022.dvs” and “DiffusionVectors_HBCD_pe2_03142022.dvs” into:

    C:\ProgramData\Siemens\Numaris\MriCustomer\CustomerSeq\DiffusionVectorSets\


    Note, the “ProgramData” directory may not be visible in Windows Explorer, but can be accessed by typing the path into the address bar. You may have to create the “DiffusionVectorSets” directory if it does not already exist.

4. If the file does not already exist, please create an empty text file at the location:

    C:\ProgramData\Siemens\Numaris\MriCustomer\MriSiteData\Paradigms\Local\PresentationSystemAvailable.txt


    This file is needed to ensure the pre-configured integration with the FIRMM tablet operates correctly within our protocol.

5. Please import “HBCD_NXVA30A_v2.2_32ch.exar1” and/or “HBCD_NXVA30A_v2.2_64ch.exar1” files, and copy the “HBCD_v2.2_32ch” and/or “HBCD_v2.2_64ch” protocol to your scanner’s sequence tree.
6. If you have a non-standard installation of your FIRMM tablet, where the tablet has a non-standard IP address or port, please contact Turing for directions on how to update the BOLD Add-In for the structural, fMRI and Diffusion sequences in the protocol to match your specific configuration. As distributed, the HBCD protocol assumes the FIRMM tablet is attached to the default IP address and port.

The PDF files are for your review, but please do not attempt to recreate the protocol manually from the PDFs.

**REPORTING ISSUES WITH INSTALLATION:** If you encounter issues with the installation of the sequences or study protocol, please submit a LORIS ticket with the following information:



1. Follow these steps to report discrepancies in scanner software baseline:

    Go to the "?" menu in the top-right corner of the scanner console, then select "About", then click on “System Info”; a window should pop up with the following version information:


    Numaris/X VA30A-03GR<br>
    syngo OAK_v7QR2201


    If you double click the "VA30A-03GR", it shows the build stamp, which should be


    Numaris/X VA30A.Night_20220414.2 C228547


    If the values on your system are not what is listed above, please report the values from your system.

2. Please indicate which of the four certificates you have successfully installed. Certificates are from UMinn/CMRR (EPI sequences), Johns Hopkins/KKI (SVS Sequence), Boston Children's Hospital (QALAS), and University of Pennsylvania (vNav Structural sequences)
3. Please indicate which of the sequences you have successfully installed: EPI sequences, SVS Sequence, QALAS, vNav Structural sequences
4. Please indicate what step in the sequence installation process is failing for you (i.e., which certificate/sequence you're trying to install and how it is failing, what errors you are encountering importing the final v2.x HBCD protocol).
5. If you believe you have installed the sequences correctly, but are encountering errors importing the v2.x HBCD protocol, please perform the following steps to confirm the sequences are fully installed:

   
      a. Open Dot Cockpit
   
      b. Browse the DEFAULT > Sequence Region > Customer Sequences > Default directory (accessible in the top left of the Dot Cockpit interface (see figure 1 below)
   
      c. Report whether all of the following sequences are listed as available in the right-most Dot Cockpit pane: cmrr_mbep2d_bold, cmrr_mbep2d_diff, cmrr_mdep2d_se, smm_svs_herc_hyper_avg_sp, a_tfl_vnav_hbcd, a_space_vnav_hbcd, tfl_3d_qalas
   
7. Please provide any additional information and/or further details if your issue is not related to those outlined above.

Figure 1. Check for fully installed sequences in DEFAULT > Sequence Region > Customer Sequences > Default.

![siemens_fig1](images/siemens_fig1.png)

## Operation Instructions

Operation instructions (a.k.a, SOP) can be found [here](https://hbcdstudy.atlassian.net/wiki/pages/viewpageattachments.action?pageId=85033234)


## Update History


### v2.2 (April 19, 2024)



* anat-t1w and anat-t2w now have the BOLD Add-In to enable connection to FIRMM
* fMRI and DWI scans have now all be configured to auto-open the inline display
* anat-t2w had its B0 Shim set to Standard


### v2.1 (June 30, 2023)



* SVS localizer protocols (axial and coronal) have been updated to reduce SAR:
    * RF Pulse Type: Normal -> Low SAR
    * Allowed Delay: 0 s -> 30 s
    * [Axial] TR: 4630 ms -> 4700 ms
    * [Coronal] TR: 1700 ms -> 1800 ms
* Coronal SVS localizer had its shim region set to automatic (and erroneously been set to a custom manual shim region before)
* anat-t1w had its TI changed from 1100 ms to 1060 ms (this had been incorrectly set in v2.0)


### v2.0 (June 20, 2023)



* [N4VE11] N4VE11 is no longer supported. All scanners must be upgraded to NXVA30A SP02 to run the v2.0 protocol.
* [NXVA30] DWI protocol was modified:
    * Prescan Normalize turned on (Normalize -> Prescan)
    * Dummy scans enabled before reference scans to reduce motion artifacts
* [NXVA30] SVS localizer protocol has been overhauled to improve registration with the structural scans in the spectroscopy analysis pipeline. SVS localizer was previously a single scan, but is now two separate scans: anat-t2w_desc-mrsLocAX and anat-t2w_desc-mrsLocCOR.
* [NXVA30] Separate SVS and HERCULES spectroscopy scans have now all been merged into a single sequence (ISTHMUS).
* [NXVA30] T2 structural sequence has been updated to improve contrast in infants based on consensus recommendation of the Structural MRI WG. Key changes include TR, TE, and echo train length.
* [NXVA30] T1 structural sequence has been updated to use compressed sensing acceleration to reduce scan time (previous versions used GRAPPA).
* [NXVA30] T1 and T2 structural sequences now have embedded vNavs that capture motion information during the scans.
* [NXVA30] T1 and T2 structural sequences now have distortion correction turned off (was previously set to 3D and saved separate uncorrected series).
* [NXVA30] There are now only 2 repetitions of the EPI field mapping sequences during the fMRI block (previously field mapping was repeated 3 times).


### v1.5.2 (April 1, 2023)



* [N4VE11] There are no changes to the N4VE11 protocol, so it remains at v1.4 but is included in the v1.5.1 directory.
* [NXVA30] The DWI protocol was again modified to have all derived images disabled except for FA Map. We previously tried to disable all derived images (see v1.5). However, a bug in the DWI sequence causes all derived images to be reenabled whenever the protocol is opened, unless at least one derived image is selected.


### v1.5.1 (March 16, 2023)



* [N4VE11] There are no changes to the N4VE11 protocol, so it remains at v1.4 but is included in the v1.5.1 directory.
* [NXVA30] Copy references settings were corrected for spectroscopy sequences in 32-channel protocol. Previously some scans copied the incorrect information, leading to runtime errors.
* [NXVA30] To assist in reproducible subject registration, the protocol folders have been set to:
    * Table Mode -> Fixed
    * Anatomy -> Brain


### v1.5 (January 25, 2023)



* [N4VE11] There are no changes to the N4VE11 protocol, so it remains at v1.4 but is included in the v1.5 directory.
* [NXVA30] Sequences were renamed to match their primary BIDS output
* [NXVA30] The following protocol changes were made to DWI scans:
    * Prescan Normalize turned off (Normalize -> Off)
    * All derived images (e.g., FA Map) turned off on Diff card
    * Fat Saturation mode changed to enable RF saturation (Fat-Water Contrast -> Fat Saturation)
* [NXVA30] The following protocol changes were made to fMRI and topup scans to harmonize across vendors:
    * FoV Read -> 224 mm
    * Base Resolution -> 112
    * Echo Spacing -> 0.54 ms
    * Bandwidth -> 2350 Hz/px
* [NXVA30] The SVS Localizer had its coronal slices increased from 1 to 5 to support better localization of relevant anatomy.
* [NXVA30] QALAS protocol changes:
    * Distortion Correction -> Off
    * Image Scaling -> 3.0


### v1.4.1 (October 6, 2022)



* [N4VE11] There are no changes to the N4VE11 protocol, so it remains at v1.4 but is included in the v1.4.1 directory.
* [NXVA30] Corrected the automatic FOV-copying links for resting state fMRI in 32-channel protocol.
* [NXVA30] Added the "Set Strategy To Fixed" step to the start of the protocols, ensuring that the table remains stationary for the duration of the scan session.
* [NXVA30] Added the "BOLD add in" to the fMRI and DWI scans, pre-populated with default information to enable support for the FIRMM tablet.


### v1.4 (August 3, 2022)



* First release at NXVA30A
* [NXVA30] T2w_SPACE now uses CS factor of 4 instead of 2x2 GRAPPA
* [NXVA30 and N4VE11] Now include up-to-date diffusion direction files with the protocol. Also confirmed that diffusion protocol is using these up-to-date direction files.
* [NXVA30 and N4VE11] Changed default location of SVS voxel to isocenter and default alignment to transversal.


### v1.3 (July 14, 2022)



* Localizer_SVS has been changed to a HASTE-based protocol.


### v1.2 (June 28, 2022)



* SpinEchoFieldMap_AP, SpinEchoFieldMap_PA, and rfMRI_REST_PA, had the following adjustments to prevent triggering the peripheral nerve stimulation model:
    * FOV 216 mm
    * Matrix Size 108 pixels
    * Bandwidth 2204 Hz/Px
    * Echo Spacing 0.56 ms
* QALAS3d_1p3mm_R2 had its FOV unlinked from T2w_SPACE, and is now set manually. tfl_b1map is now set to default its FOV to follow QALAS3d_1p3mm.


### v1.1.2 (June 20, 2022)



* SpinEchoFieldMap_AP, SpinEchoFieldMap_PA, and rfMRI_REST_PA, corrected to have pure axial orientation for FOV (was previously angled T > C).


### v1.1.1 (June 16, 2022)



* DWI_pe2_AP correct to no longer wait for user before starting; this was missed in the previous v1.1 release.
* Corrected Localizer_SVS to have “Body part examined” set to “Brain”. This was missed in the previous v1.1 release.


### v1.1 (June 13, 2022)



* Replaced Localizer with Localizer_quiet, based on Baby Connectome Project localizer (with addition of "Acoustic Noise Reduction" filter) to reduce acoustic noise.
* FOV for QALAS3d_1p3mm_R2, tfl_b1map, and T1w_MPR have now been set to default to follow the FOV for T2w_SPACE.
* DWI_pe1_AP and DWI_pe2_AP have now been set to use their FOV as the default shim volume (was previously a manual volume).
* FOV of DWI_pe2_AP has now been set to default to follow FOV for DWI_pe1_AP.
* Default FOV of DWI scans has been moved to L0 P0 H6, matching initial fMRI FOV.
* PRESS35 and HERC sequences have now been set to use their voxel as the default shim volume (was previously a manual volume).
* PRESS35_unsupp and HERC_unsupp now have parameter Sequence > Common > Delta frequency set to 0.0 ppm (was previously -1.7 ppm).
* Voxel of PRESS35_unsupp, HERC, and HERC_unsupp have now been set to follow the voxel for PRESS35.
* Added Localizer_SVS before PRESS35 scan, to provide anatomical localizer for SVS sequence. This sequence is somewhat louder than Localizer_quiet, but is shorter and has greater axial coverage.
* In 64-channel protocol, tfl_b1map was moved up in scan order to follow QALAS3d_1p3mm_R2 (now matches 32-channel protocol). 
* "Wait for start" has been removed from all sequences to ensure back-to-back play-through, minimizing silent "gaps".
* Positioning mode of all sequences has been set to FIX (previously had mix of REF and FIX modes)
* T2w_SPACE now has filter mode set explicitly, removing dependence on "implicit filter" settings on individual scanners.
* T2w_SPACE now has default image scaling set to 2 (was previously 1)
* DWI_pe1_AP and DWI_pe2_AP had their TEs set to 88 ms (was previously 87.40 ms)
* All scans have "Body part examined" set to "Brain".


### v1.0 (April 19, 2022)

Initial release.


## Download v2.2 Sequences
[HBCD_v2.2_32ch.pdf](v2.2_sequences/siemens/HBCD_v2.2_32ch.pdf)<br>
[HBCD_v2.2_64ch.pdf](v2.2_sequences/siemens/HBCD_v2.2_64ch.pdf)<br>
[HBCD_v2.2_32ch.exar1](v2.2_sequences/siemens/HBCD_v2.2_32ch.exar1)<br>
[HBCD_v2.2_64ch.exar1](v2.2_sequences/siemens/HBCD_v2.2_64ch.exar1)<br>
[DiffusionVectors_HBCD_pe1_03142022.dvs](v2.2_sequences/siemens/DiffusionVectors_HBCD_pe1_03142022.dvs)<br>
[DiffusionVectors_HBCD_pe2_03142022.dvs](v2.2_sequences/siemens/DiffusionVectors_HBCD_pe2_03142022.dvs)
