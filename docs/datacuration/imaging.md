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

### B1 Fieldmaps
Siemens, GE, and Philips will include additional files under `fmap/` due to acquisition of B1 fieldmaps, which were converted following the BIDS specification for quantitative MRI (see BIDS specific notes for [TB1TFL and TB1RFM](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1tfl-and-tb1rfm-specific-notes) and [TB1AFI](https://bids-specification.readthedocs.io/en/stable/appendices/qmri.html#tb1afi-specific-notes)). The Siemens label `acq-<anat/fmap>` denotes the anatomical (like) image and scaled flip angle map and the GE and Philips label `acq-tr<1/2>` denotes the first and second TR image.
```
...
|   |__ ses-<label>/
|       |__ fmap/
|           |
|     SIEMENS ONLY:
|           |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.nii.gz
|           |__ sub-<label>_ses-<label>_acq-anat_run-<label>_TB1TFL.json
|           |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.nii.gz
|           |__ sub-<label>_ses-<label>_acq-fmap_run-<label>_TB1TFL.json
|           |
|     GE/PHILIPS ONLY:
|           |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.nii.gz 
|           |__ sub-<label>_ses-<label>_acq-tr1_run-<label>_TB1AFI.json 
|           |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.nii.gz
|           |__ sub-<label>_ses-<label>_acq-tr2_run-<label>_TB1AFI.json
```

### MR Spectroscopy
Unlike the other MRI modalities, MRS data was converted to BIDS using [spec2nii v0.7.0](https://github.com/wtclarke/spec2nii). The BIDS files include two sets of metabolite (`*_svs.nii.gz`) and water reference (`*_ref.nii.gz`) data aqcuired via short-echo-time (TE = 35 ms) (`acq-shortTE`) and HERCULES (spectral-edited, TE = 80 ms) (`acq-hercules`). The JSON sidecar files include the dimensions of the NIfTI-MRS data array, holding different coil elements in dimension 5 and different transients in dimension 6.
```
...
|   |__ ses-<label>/
|       |__ mrs/
|       |   |__ sub-<label>_ses-<label>_acq-shortTE_run-<label>_svs.nii.gz
|       |   |__ sub-<label>_ses-<label>_acq-shortTE_run-<label>_svs.json
|       |   |__ sub-<label>_ses-<label>_acq-shortTE_run-<label>_ref.nii.gz
|       |   |__ sub-<label>_ses-<label>_acq-shortTE_run-<label>_ref.json
|       |   |__ sub-<label>_ses-<label>_acq-hercules_run-<label>_svs.nii.gz
|       |   |__ sub-<label>_ses-<label>_acq-hercules_run-<label>_svs.json
|       |   |__ sub-<label>_ses-<label>_acq-hercules_run-<label>_ref.nii.gz
|       |   |__ sub-<label>_ses-<label>_acq-hercules_run-<label>_ref.json
```

## Post-Conversion Modifications
<details>
<summary><b>Hard-coded fields for missing/incorrect header information</b></summary>
<br>
In some instances, the NIfTI and JSON files obtained from the <code>dcm2niix</code> conversion needed to be altered by in-house scripts to resolve conversion errors. One common error was JSON headers that were either missing or incorrectly set. The headers for the filetypes listed below were hard-coded post-conversion to resolve these errors. Hard-coded headers are also listed in the <code>HardCodedValues</code> field of the JSON sidecar file.  
<br>
<br>
<ul>
<b>Philips</b>
	<li>T1W: `RepetitionTime`</li>
	<li>DWI: `PhaseEncodingDirection`, `TotalReadoutTime`, &amp; `SliceTiming` (`SmallDelta` and `LargeDelta` also added)</li>
	<li>EPI: `PhaseEncodingDirection` &amp; `TotalReadoutTime`</li>
	<li>BOLD:	`PhaseEncodingDirection`, `TotalReadoutTime`, &amp; `SliceTiming`</li>
<br>
<b>GE</b>
	<li>T1W: `RepetitionTime`</li>
</ul>
</details>

<details>
<summary><b>Quantitative MRI</b></summary><br>
Depending on scanner manufacturer, QALAS conversion resulted in either five 3D NIfTI files or one 4D NIfTIs with 5 volumes. All QALAS series were thus converted to five NIfTIs with different inversion times (labeled using the <code>inv-&lt;label&gt;</code> BIDS entity) and the JSON sidecar was modified with the following:
<ul>
<br>
<code>InversionTime</code> values were hard-coded as follows:
  <li>0 in the <code>inv-0</code> QALAS file</li>
  <li>0.1 in the <code>inv-1</code> QALAS file</li>
  <li>1 in the <code>inv-2</code> QALAS file</li>
  <li>1.9 in the <code>inv-3</code> QALAS file</li>
  <li>2.7 in the <code>inv-4</code> QALAS file</li><br>
<code>T2Prep</code> hard-coded as 0.1 in the <code>inv-0</code> QALAS file
</ul>
</details><br>