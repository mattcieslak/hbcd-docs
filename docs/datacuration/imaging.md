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

The above includes EPI fieldmaps under `fmap/`. However, Siemens, GE, and Philips have B1 fieldmaps and follow [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#quantitative-mri):

For **Siemens**, anatomical (like) images and scaled flip angle maps are annotated with `acq-anat` and `acq-fmap` labels, respectively (see [BIDS spec](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes)):
```
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.json 
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.nii.gz
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.json
```

For **GE and Philips**, the first and second TR image are annotated with `acq-tr1` and `acq-tr2`, respectively: 
```
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.json 
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.nii.gz
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.json
```

## Post-Conversion Modifications
In some instances, the NIfTI and JSON files obtained from the dcm2niix conversion needed to be altered by in-house script to include additional header information. Any hard-coded headers are listed in the `HardCodedValues` field of the JSON sidecar file of the acquisition.

### ANAT/      
**Philips T1W**: `RepetitionTime` incorrectly set, so was hardcoded to reflect the actual repetition time of the acquisition

**Quantitative MRI**: Either 5 NIfTI 3D files or 1 NIfTI 4D file with 5 volumes produced depending on scanner manufacturer and there was missing header information from JSON. All QALAS series were thus converted to 5 NIfTI files with different inversion times (labeled using the `inv-<label>` BIDS entity) and the JSON sidecar was modified with the following:

<details>
<summary><i>[Click to expand]</i></summary>
<ul>
<br>
`InversionTime` values were hard-coded as follows:
  <li>0 in the `inv-0` QALAS file</li>
  <li>0.1 in the `inv-1` QALAS file</li>
  <li>1 in the `inv-2` QALAS file</li>
  <li>1.9 in the `inv-3` QALAS file</li>
  <li>2.7 in the `inv-4` QALAS file</li><br>
`T2Prep` was hard-coded as 0.1 in the `inv-0` QALAS file
</ul>
</details><br>

### DWI/     
**Philips DWI**: `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information missing, so were hard-coded into JSON sidecar file. `SmallDelta` and `LargeDelta` header values have also been added to all DWI JSON sidecar files.

### FMAP/
**Philips EPI Images**: `PhaseEncodingDirection` and `TotalReadoutTime` header information missing, so were hard-coded into JSON sidecar file

**GE B1 Map**: `RepetitionTime` field needed to be hard-coded to 0.015 for `acq-tr1` and 0.075 for `acq-tr2` as it was not properly populated by the conversion tool

### FUNC/
**Philips BOLD**: `PhaseEncodingDirection`, `TotalReadoutTime`, and `SliceTiming` header information missing. Those headers have been hard-coded in the JSON sidecar file for Philips BOLD acquisitions.

