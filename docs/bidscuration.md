# Data Curation and Creation of the HBCD BIDS Dataset

As much as possible, HBCD processing tries to utilize the [Brain Imaging Data Structure](https://bids-specification.readthedocs.io/en/stable/) (BIDS) standard for data organization. At a high level, the HBCD BIDS structure will appear as follows:

![](./../images/bids.png)

As anticipated in a large infant study, many subjects will have missing data elements. As a result, the number of folders and files available for each unique subject and session will vary. Additionally, because the HBCD acquisition involves multiple modalities, some are collected at different times. Even within a single modality, certain acquisitions may be gathered on different days.

## Participants level data
Participant level data is available in the `participants.tsv` file, located at the root directory of the BIDS dataset. This file contains information about the participants’ sex. Descriptions of the TSV column names and properties of their values can be found in the sidecar `participants.json` file.

## Sessions level data
Session level data is available in the `sessions.tsv` file located in the subject folder. This file contains information about the different sessions acquired for the participant in question. This file contains information about the site of collection, the age and gestational age of the participant during the sessions, and the head size of the participant. Descriptions of the TSV column names and properties of their values can be found in the sidecar `sessions.json` file.

*Note: age measures are computed based on a birthdate measure that is jittered up to 7 days.*

## Scans level data
The complexity of data acquisition and the varying image quality across scans make the `scans.tsv` file, located in the session folder. This file contains information about how old the participant was at the time of the acquisition, and in certain cases there is also information about the quality of the underlying acquisition. To get a better understanding of what the different fields in the `scans.tsv` file mean, please refer to the `scans.json` file.

*Note: age measures are computed based on a birthdate measure that is jittered up to 7 days.*

## MRI data curation and conversion to BIDS
DICOM images are converted using a [custom version](https://github.com/rordenlab/dcm2niix/tree/c5caaa9f858b704b61d3ff4a7989282922dd712e) of the [dcm2niix](https://github.com/rordenlab/dcm2niix) tool that included bug fixes for some modalities acquired in HBCD.

MRI protocol is then checked in the produced NIfTI and JSON files and some exclusion criteria have been developed to ensure the quality of the data. For example, we check that all images are acquired using a head coil before including them in the BIDS dataset. Other exclusion criteria will be detailed in each of the image type sections below.

In some instances, the NIfTI and JSON files obtained from the dcm2niix conversion needed to be altered by in house script to include additional header information. Those changes will be listed below in each of the image type sections below. Any hard-coded headers are listed in the HardCodedValues field of the JSON sidecar file of the acquisition..  

### Anatomical images
#### T1W
T1W images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_run-<label>_T1w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

In the case of the Philips T1W images, the RepetitionTime value obtained after the dcm2niix conversion was incorrectly set and needed to be hardcoded to reflect the actual repetition time of the acquisition. 

**Exclusion Criteria**
- TR outside of range 2.3-2.41  
- TE outside of range 0.002-0.0035  
- TI outside of range 1.06-1.1  
- Slice thickness not being 0.8 

#### T2W
T2W images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_run-<label>_T2w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

The following exclusion criteria has been set to exclude any acquisition with:
- TR outside of range 2.5-4.5  
- TE outside of range 0.09-0.15  
- TI outside of range 0.29-0.33  
- Slice thickness outside of range 0.563-0.565

#### MRS localizer
MRS localizer images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_T2w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

Axial MRS localizers are labeled using the acq-mrsLocAx label and coronal MRS localizers are labeled using the acq-mrsLocCor label.

**Exclusion Criteria**
- TR outside of range 2.5-4.5  
- TE outside of range 0.09-0.15  
- TI outside of range 0.29-0.33  
- Slice thickness outside of range 0.563-0.565

#### QALAS
QALAS images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_run-<label>_inv-<label>_QALAS.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

Depending on the scanner manufacturer, dcm2niix produced either 5 NIfTI 3D files or 1 NIfTI 4D file with 5 volumes. In addition, some header information was missing from the JSON file produced by dcm2niix. Therefore, we took the files produced by dcm2niix and generated the QALAS NIfTI files that can be found in the BIDS dataset. Therefore, each QALAS series results in 5 NIfTI files with different inversion time (labeled using the inv-\<label\> BIDS tag). In addition, JSON sidecar file needed have the following headers modified:

InversionTime values were hard-coded as follows:   
- 0 in the `inv-0` QALAS file  
- 0.1 in the `inv-1` QALAS file  
- 1 in the `inv-2` QALAS file  
- 1.9 in the `inv-3` QALAS file  
- 2.7 in the `inv-4` QALAS file  

T2Prep was hard-coded as 0.1 in the `inv-0` QALAS file

### Diffusion weighted images
DWI images can be found in the dwi subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_dir-<label>_run-<label>_dwi.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The label `dir-<label>` is used to distinguish between the DWI acquired in the AP phase encoding direction (dir-AP) and the DWI acquired in the PA phase encoding direction (dir-PA).

Philips DWI files obtained after the dcm2niix conversion were missing the PhaseEncodingDirection, TotalReadoutTime, and SliceTiming header information. Those headers have been hard-coded in the JSON sidecar file for Philips DWI acquisitions.

SmallDelta and LargeDelta header values have also been added to all DWI JSON sidecar files.

**Exclusion Criteria**
- TR not being set to 4.8  
- TE outside of range 0.0880-0.0980  
- Slice thickness not being set to 1.7  
- The total number of volumes between DWI AP and DWI PA is below 90 volumes

### Fieldmap images
#### EPI images
EPI images can be found in the fmap subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_dir-<label>_run-<label>_epi.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The label `dir-<label>` is used to distinguish between the EPI acquired in the AP phase encoding direction (dir-AP) and the EPI acquired in the PA phase encoding direction (dir-PA).

Philips EPI files obtained after the dcm2niix conversion were missing the PhaseEncodingDirection and TotalReadoutTime header information. Those headers have been hard-coded in the JSON sidecar file for Philips EPI acquisitions.

**Exclusion Criteria**
- TR outside of range 8.4-9.2  
- TE outside of range 0.064-0.0661  
- TI not being set to 2  
- Slice thickness outside of range 0.563-0.565

#### Siemens B1 map
Siemens B1 images can be found in the fmap subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_TB1TFL.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. Anatomical (like) image for this acquisition is labeled acq-anat and scaled flip angle map is labeled `acq-fmap` as specified in the [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes).

#### GE and Philips B1 map
Siemens B1 images can be found in the fmap subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_TB1AFI.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The first TR image for this acquisition is labeled acq-tr1 and the second TR image is labeled `acq-tr2` as specified in the [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes).

For GE scanners, the **RepetitionTime** field needed to be hard-coded to 0.015 for `acq-tr1` and 0.075 for `acq-tr2` as it was not properly populated by the conversion tool.

### Functional BOLD images
BOLD images can be found in the func subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_task-rest_dir-PA_run-<label>_bold.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

Philips BOLD files obtained after the dcm2niix conversion were missing the PhaseEncodingDirection, TotalReadoutTime, and SliceTiming  header information. Those headers have been hard-coded in the JSON sidecar file for Philips BOLD acquisitions.

**Exclusion Criteria**
- TR not being set to 1.725  
- TE outside of range 0.0369-0.0371  
- Slice thickness not being set to 2  
- fMRI is shorter than 87 volumes (approximately less than 2.5 minutes long)

### Spectroscopy images

## EEG data curation and conversion to BIDS

## Motion data curation and conversion to BIDS

## Phenotypes data curation and conversion to BIDS
