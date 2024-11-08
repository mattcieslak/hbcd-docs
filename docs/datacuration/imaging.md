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

### B1 fieldmaps
In addition to what's shown above, Siemens, GE, and Philips include acquisition of B1 fieldmaps, which were converted following the [BIDS specification for quantitative MRI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#quantitative-mri):

**SIEMENS**   
Anatomical (like) images and scaled flip angle maps are annotated with `acq-anat` and `acq-fmap` labels, respectively (see [TB1TFL and TB1RFM specific notes](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes) of BIDS spec):
```
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.json 
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.nii.gz
|   |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.json
```

**GE and PHILIPS**    
The first and second TR image are annotated with `acq-tr1` and `acq-tr2`, respectively (see [TB1AFI specific notes](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1afi-specific-notes) of BIDS spec): 
```
|__ fmap/
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.nii.gz 
|   |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.json 
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.nii.gz
|   |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.json
```

## Post-Conversion Modifications
In some instances, the NIfTI and JSON files obtained from the `dcm2niix` conversion needed to be altered by in-house scripts to resolve conversion errors.

**Missing/Incorrect Header Information**    
The following headers were hardcoded post-conversion either due to missing or incorrectly set values (hard-coded headers are also listed in the `HardCodedValues` field of the JSON sidecar file of the acquisition): 

- Philips:
    - T1W: `RepetitionTime`
    - DWI: `PhaseEncodingDirection`, `TotalReadoutTime`, & `SliceTiming` (`SmallDelta` and `LargeDelta` also added)
    - EPI: `PhaseEncodingDirection` & `TotalReadoutTime`
    - BOLD:	`PhaseEncodingDirection`, `TotalReadoutTime`, & `SliceTiming`
- GE:
    - B1 Map: `RepetitionTime` (hard-coded to 0.015 for `acq-tr1` and 0.075 for `acq-tr2`)


**Quantitative MRI**    
Depending on scanner manufacturer, QALAS conversion resulted in either five 3D NIfTI files or one 4D NIfTIs with 5 volumes. All QALAS series were thus converted to five NIfTIs with different inversion times (labeled using the `inv-<label>` BIDS entity) and the JSON sidecar was modified with the following:

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