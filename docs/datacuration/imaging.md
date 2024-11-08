# Imaging Data Curation & BIDS Conversion

## BIDS Conversion
DICOM images are converted using a [custom version](https://github.com/rordenlab/dcm2niix/tree/c5caaa9f858b704b61d3ff4a7989282922dd712e) of the [dcm2niix](https://github.com/rordenlab/dcm2niix) tool customized for HBCD. The resulting data structure is: 

```
assembly_bids/ 
|__ participants.tsv
|__ participants.json 
|__ sub-<label>/
|   |__ sub-<label>_sessions.tsv
|   |__ sub-<label>_sessions.json
|   |__ ses-<label>/
|       |
|       |__ anat/
|       |   |__ sub-<label>_ses-<label>_run-<label>_T1w.nii.gz 
|       |   |__ sub-<label>_ses-<label>_run-<label>_T1w.json
|       |   |__ sub-<label>_ses-<label>_run-<label>_T2w.nii.gz
|       |   |__ sub-<label>_ses-<label>_run-<label>_T2w.json
|       |   |__ sub-<label>_ses-<label>_acq-<mrsLocAx/mrsLocCor>_run-<label>_T2w.nii.gz 
|       |   |__ sub-<label>_ses-<label>_acq-<mrsLocAx/mrsLocCor>_run-<label>_T2w.json
|       |   |__ sub-<label>_ses-<label>_run-<label>_inv-<label>_QALAS.nii.gz
|       |   |__ sub-<label>_ses-<label>_run-<label>_inv-<label>_QALAS.json
|       |
|       |__ dwi/
|       |   |__ sub-<label>_ses-<label>_dir-AP_run-<label>_dwi.nii.gz
|       |   |__ sub-<label>_ses-<label>_dir-AP_run-<label>_dwi.json
|       |   |__ sub-<label>_ses-<label>_dir-PA_run-<label>_dwi.nii.gz
|       |   |__ sub-<label>_ses-<label>_dir-PA_run-<label>_dwi.json
|       |
|       |__ fmap/
|       |   |__ sub-<label>_ses-<label>_dir-AP_run-<label>_epi.nii.gz
|       |   |__ sub-<label>_ses-<label>_dir-AP_run-<label>_epi.json
|       |   |__ sub-<label>_ses-<label>_dir-PA_run-<label>_epi.nii.gz
|       |   |__ sub-<label>_ses-<label>_dir-PA_run-<label>_epi.json
|       |
|       |__ func/
|       |   |__ sub-<label>_ses-<label>_task-rest_dir-PA_run-<label>_bold.nii.gz
|       |   |__ sub-<label>_ses-<label>_task-rest_dir-PA_run-<label>_bold.json
|       |   
|       |__ sub-<label>_ses-<label>_scans.tsv
|       |__ sub-<label>_ses-<label>_scans.json
```

The above includes EPI fieldmaps under `fmap/`. However, Siemens, GE, and Philips fieldmaps are different and will instead look like:
```
Siemens B1 Map
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.json 
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.nii.gz
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.json

GE and Philips B1 Map
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.json 
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.nii.gz
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.json
```
In some instances, the NIfTI and JSON files obtained from the dcm2niix conversion needed to be altered by in-house script to include additional header information. Those changes are listed below in each of the image type sections below. Any hard-coded headers are listed in the `HardCodedValues` field of the JSON sidecar file of the acquisition.

## Modalities
### Anatomical Images  
T1w: `anat/sub-<label>_ses-<label>_run-<label>_T1w.nii.gz`      
T2w: `anat/sub-<label>_ses-<label>_run-<label>_T2w.nii.gz`

**Post-Conversion Modifications**        
For Philips T1W images, the `RepetitionTime` value obtained after the dcm2niix conversion was incorrectly set and needed to be hardcoded to reflect the actual repetition time of the acquisition.

### MRS Localizer
Axial MRS localizers: `anat/sub-<label>_ses-<label>_acq-mrsLocAx_run-<label>_T2w.nii.gz`      
Coronal MRS localizers: `anat/sub-<label>_ses-<label>_acq-mrsLocCor_run-<label>_T2w.nii.gz`

### Quantitative MRI
Filename: `anat/sub-<label>_ses-<label>_run-<label>_inv-<label>_QALAS.nii.gz` 

**Post-Conversion Modifications**   
Depending on the scanner manufacturer, dcm2niix produced either 5 NIfTI 3D files or 1 NIfTI 4D file with 5 volumes. In addition, some header information was missing from the JSON file produced by `dcm2niix`. Therefore, we took the files produced by `dcm2niix` and generated the QALAS NIfTI files that can be found in the BIDS dataset. Therefore, each QALAS series results in 5 NIfTI files with different inversion time (labeled using the `inv-<label>` BIDS tag). In addition, JSON sidecar file needed to have the following headers modified:

- `InversionTime` values were hard-coded as follows:   
    - 0 in the `inv-0` QALAS file  
    - 0.1 in the `inv-1` QALAS file  
    - 1 in the `inv-2` QALAS file  
    - 1.9 in the `inv-3` QALAS file  
    - 2.7 in the `inv-4` QALAS file  

- `T2Prep` was hard-coded as 0.1 in the `inv-0` QALAS file

### Diffusion 
Acquired in AP phase encoding direction: `dwi/sub-<label>_ses-<label>_dir-AP_run-<label>_dwi.nii.gz`    
Acquired in PA phase encoding direction: `dwi/sub-<label>_ses-<label>_dir-PA_run-<label>_dwi.nii.gz` 

**Post-Conversion Modifications**     
After `dcm2niix` conversion, Philips DWI files were missing `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information. These headers have been hard-coded into the JSON sidecar file for Philips DWI acquisitions. `SmallDelta` and `LargeDelta` header values have also been added to all DWI JSON sidecar files.

### Fieldmap Images
#### EPI Images
EPI acquired in the AP phase encoding direction: `fmap/sub-<label>_ses-<label>_dir-AP_run-<label>_epi.nii.gz`    
EPI acquired in the PA phase encoding direction: `fmap/sub-<label>_ses-<label>_dir-PA_run-<label>_epi.nii.gz`

**Post-Conversion Modifications**   
After `dcm2niix` conversion, Philips EPI files were missing `PhaseEncodingDirection` and `TotalReadoutTime` header information. These headers have now been hard-coded into the JSON sidecar file for Philips EPI acquisitions.

#### Siemens B1 Map
Anatomical (like) image for acquisition: `fmap/sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.nii.gz`       
Scaled flip angle map: `fmap/sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.nii.gz` 

See [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes).

#### GE and Philips B1 Map
First TR image: `fmap/sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.nii.gz`    
Second TR image: `fmap/sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.nii.gz`

See [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes). 

**Post-Conversion Modifications**   
For GE scanners, the `RepetitionTime` field needed to be hard-coded to 0.015 for `acq-tr1` and 0.075 for `acq-tr2` as it was not properly populated by the conversion tool.

### Functional BOLD
Filenames: `func/sub-<label>_ses-<label>_task-rest_dir-PA_run-<label>_bold.nii.gz`  

**Post-Conversion Modifications**   
Philips BOLD files obtained after the `dcm2niix` conversion were missing the `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information. Those headers have been hard-coded in the JSON sidecar file for Philips BOLD acquisitions.

### Spectroscopy


