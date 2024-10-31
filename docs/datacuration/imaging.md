# Imaging Data Curation & BIDS Conversion

## Quality Control
Quality control of the MRI images can be found in the `scans.tsv` file in the session folder. The raw QC process involves reviewing unprocessed or lightly processed MRI data to identify and exclude data with severe artifacts from further processing. An initial protocol compliance check is performed by extracting information from DICOM headers and checking for common issues and protocol deviations, such as missing files or incorrect patient orientation. Automated QC metrics are calculated from the image data. A deep learning model estimates motion artifacts for structural scans (T1w, T2w, and qMRI), while metrics related to motion, bad frames, line artifacts, and FOV (field of view) cutoff are assessed for dMRI, fMRI, and field maps. A subset of series are selected for manual review based on multivariate prediction and Bayesian classifiers using the automated metrics. During the manual review, data quality is scored based on the severity of specific artifacts. For structural scans, motion artifacts are scored based on perceived severity on a scale of 0 to 3. Scores indicate no artifact (0), mild (1), moderate (2), or severe (3). Other artifacts, such as unusual intensity inhomogeneity or ghosting are noted by the reviewer. For dMRI, fMRI, and field maps, scored artifacts include susceptibility artifacts, FOV cutoff, and line artifacts. Other artifacts may be noted. Series with severe artifacts that clearly compromise data usability are rejected (QC=0).

## MRI
DICOM images are converted using a [custom version](https://github.com/rordenlab/dcm2niix/tree/c5caaa9f858b704b61d3ff4a7989282922dd712e) of the [dcm2niix](https://github.com/rordenlab/dcm2niix) tool that included bug fixes for some modalities acquired in HBCD.

The MRI protocol is then checked in the produced NIfTI and JSON files in which certain exclusion criteria have been developed to ensure the quality of the data. For example, a check to ensure that all images are acquired using a head coil was performed before including it in the BIDS dataset. Other exclusion criteria will be detailed in each of the image type sections below.

In some instances, the NIfTI and JSON files obtained from the dcm2niix conversion needed to be altered by in-house script to include additional header information. Those changes are listed below in each of the image type sections below. Any hard-coded headers are listed in the `HardCodedValues` field of the JSON sidecar file of the acquisition.

### Anatomical Images
#### T1W
T1W images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_run-<label>_T1w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

For Philips T1W images, the `RepetitionTime` value obtained after the dcm2niix conversion was incorrectly set and needed to be hardcoded to reflect the actual repetition time of the acquisition. 

**Exclusion Criteria**    
- TR outside of range 2.3-2.41  
- TE outside of range 0.002-0.0035  
- TI outside of range 1.06-1.1  
- Slice thickness not being 0.8 

#### T2W
T2W images can be found in the anat subdirectory located in the session folder. They are labeled as `sub-<label>_ses-<label>_run-<label>_T2w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

**Exclusion Criteria**    
- TR outside of range 2.5-4.5  
- TE outside of range 0.09-0.15  
- TI outside of range 0.29-0.33  
- Slice thickness outside of range 0.563-0.565

#### MRS localizer
MRS localizer images can be found in the anat subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_T2w.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. Axial MRS localizers are labeled using the `acq-mrsLocAx` label and coronal MRS localizers are labeled using the `acq-mrsLocCor` label.

**Exclusion Criteria**
- TR outside of range 2.5-4.5  
- TE outside of range 0.09-0.15  
- TI outside of range 0.29-0.33  
- Slice thickness outside of range 0.563-0.565

#### Quantitative MRI
QALAS images can be found in the anat subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_run-<label>_inv-<label>_QALAS.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. 

Depending on the scanner manufacturer, dcm2niix produced either 5 NIfTI 3D files or 1 NIfTI 4D file with 5 volumes. In addition, some header information was missing from the JSON file produced by `dcm2niix`. Therefore, we took the files produced by `dcm2niix` and generated the QALAS NIfTI files that can be found in the BIDS dataset. Therefore, each QALAS series results in 5 NIfTI files with different inversion time (labeled using the `inv-<label>` BIDS tag). In addition, JSON sidecar file needed to have the following headers modified:

`InversionTime` values were hard-coded as follows:   
- 0 in the `inv-0` QALAS file  
- 0.1 in the `inv-1` QALAS file  
- 1 in the `inv-2` QALAS file  
- 1.9 in the `inv-3` QALAS file  
- 2.7 in the `inv-4` QALAS file  

`T2Prep` was hard-coded as 0.1 in the `inv-0` QALAS file

### Diffusion 
DWI images can be found in the dwi subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_dir-<label>_run-<label>_dwi.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The label `dir-<label>` is used to distinguish between the DWI acquired in the AP phase encoding direction (`dir-AP`) and the DWI acquired in the PA phase encoding direction (`dir-PA`). *Note:* After `dcm2niix` conversion, Philips DWI files were missing `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information. These headers have been hard-coded into the JSON sidecar file for Philips DWI acquisitions. `SmallDelta` and `LargeDelta` header values have also been added to all DWI JSON sidecar files.

**Exclusion Criteria**
- TR not being set to 4.8  
- TE outside of range 0.0880-0.0980  
- Slice thickness not being set to 1.7  
- The total number of volumes between DWI AP and DWI PA is below 90 volumes

### Fieldmap Images
#### EPI Images
EPI images can be found in the fmap subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_dir-<label>_run-<label>_epi.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The label `dir-<label>` is used to distinguish between the EPI acquired in the AP phase encoding direction (`dir-AP`) and the EPI acquired in the PA phase encoding direction (`dir-PA`). *Note:* After `dcm2niix` conversion, Philips EPI files were missing `PhaseEncodingDirection` and `TotalReadoutTime` header information. These headers have now been hard-coded into the JSON sidecar file for Philips EPI acquisitions.

**Exclusion Criteria**
- TR outside of range 8.4-9.2  
- TE outside of range 0.064-0.0661  
- TI not being set to 2  
- Slice thickness outside of range 0.563-0.565

#### Siemens B1 Map
Siemens B1 images can be found in the fmap subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_TB1TFL.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. Anatomical (like) image for this acquisition is labeled `acq-anat` and scaled flip angle map is labeled `acq-fmap` as specified in the [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes).

#### GE and Philips B1 Map
Siemens B1 images can be found in the fmap subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_acq-<label>_run-<label>_TB1AFI.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. The first TR image for this acquisition is labeled `acq-tr1` and the second TR image is labeled `acq-tr2` as specified in the [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes). *Note:* For GE scanners, the `RepetitionTime` field needed to be hard-coded to 0.015 for `acq-tr1` and 0.075 for `acq-tr2` as it was not properly populated by the conversion tool.

### Functional BOLD
BOLD images can be found in the func subdirectory located in the session folder, labeled as `sub-<label>_ses-<label>_task-rest_dir-PA_run-<label>_bold.nii.gz`. The JSON sidecar file contains relevant header information about the acquisition. *Note:* Philips BOLD files obtained after the `dcm2niix` conversion were missing the `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information. Those headers have been hard-coded in the JSON sidecar file for Philips BOLD acquisitions.

**Exclusion Criteria**
- TR not being set to 1.725  
- TE outside of range 0.0369-0.0371  
- Slice thickness not being set to 2  
- fMRI is shorter than 87 volumes (approximately less than 2.5 minutes long)

### Spectroscopy
