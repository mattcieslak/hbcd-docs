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
For MRS, vendor-specific raw data formats (Siemens .dat; Philips data/list; GE P-file) were converted to BIDS using [spec2nii v0.7.0](https://github.com/wtclarke/spec2nii). Output files include metabolite and water reference (`*_<svs/ref>.nii.gz`) data aqcuired via short-echo-time (TE = 35 ms) and HERCULES (spectral-edited, TE = 80 ms) (`acq-<shortTE/hercules>`). The JSON sidecar files include the dimensions of the NIfTI-MRS data array, holding different coil elements in dimension 5 and different transients in dimension 6.
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
<p>
<details>
<summary><b>Hard-coded fields for missing/incorrect header information</b></summary>
<br>
In some cases, <i>dcm2niix</i> conversion led to missing or incorrectly configured NIfTI/JSON metadata. To address these issues, the headers for the file types listed below were hard-coded after conversion. These hard-coded values are also documented in the <i>HardCodedValues</i> field of the corresponding JSON sidecar file.
<br>
<br>
<ul>
<b>Philips</b>
	<li>T1W: <i>RepetitionTime</i></li>
	<li>DWI: <i>PhaseEncodingDirection</i>, <i>TotalReadoutTime</i>, & <i>SliceTiming</i> (<i>SmallDelta</i> & <i>LargeDelta</i> also added)</li>
	<li>EPI: <i>PhaseEncodingDirection</i> & <i>TotalReadoutTime</i></li>
	<li>BOLD:	<i>PhaseEncodingDirection</i>, <i>TotalReadoutTime</i>, & <i>SliceTiming</i></li>
<br>
<b>GE</b>
	<li>T1W: <i>RepetitionTime</i></li>
</ul>
</details>
</p>

<details>
<summary><b>Quantitative MRI</b></summary><br>
Depending on the scanner manufacturer, QALAS conversion produced either five 3D NIfTI files or a single 4D NIfTI file with five volumes. To standardize the output, all QALAS series were converted into five separate NIfTI files, each corresponding to a different inversion time (labeled using the <i>inv-&lt;label&gt;</i> BIDS entity). The associated JSON sidecar was then updated with the following modifications:
<ul>
<br>
<i>InversionTime</i> values were hard-coded in the QALAS files indicated as follows:
  <li><i>inv-0</i> file: hard-coded to 0</li>
  <li><i>inv-1</i> file: hard-coded to 0.1</li>
  <li><i>inv-2</i> file: hard-coded to 1</li>
  <li><i>inv-3</i> file: hard-coded to 1.9</li>
  <li><i>inv-4</i> file: hard-coded to 2.7</li>
<br>
<i>T2Prep</i> value hard-coded to 0.1 in the <i>inv-0</i> QALAS file
</ul>
</details><br>


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>REFERENCES</title>
  <style>
    .collapsible {
      background-color: #7cceb399;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
    }
    details {
      background-color: #7cceb366;
      padding: 10px;
      margin: 10px 1;
      border-radius: 5px;
    }
    summary {
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }
    a {
      color: #007BFF;
      text-decoration: none;
    }
  </style>
</html>