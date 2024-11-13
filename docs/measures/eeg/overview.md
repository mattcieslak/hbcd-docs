# Overview

## EEG Parameters

![](images/EEG_acquisition_protocol.png)

<details>
<summary>Implementation & Data Collection Details</summary>
<ul>
<br>
<p><strong>Method of Administration</strong>: RA administered in person <br />
<strong>Child Specific/Unspecific Form</strong>: Child Specific <br />
<strong>Visits</strong>: Visit 3 (3-9 months), Visit 4 (9-15 months), Visit 6 (15-48 months) <br />
<strong>Estimated length of time for completion</strong>: Video RS 3 min; Face 5 min, MMN 11.5 [V03] & 8.5 [V04/6] min; VEP 1 min</p>
</details>

## Quality Control & Known Issues 
### Quality Control Procedures   
After EEG acquisition, quality control checks are performed using [EEG2BIDS Wizard](https://github.com/aces/eeg2bids), a custom MATLAB application installed at all HBCD sites. These checks are immediately provided to the user to ensure the data's integrity and usability. The process includes:

- Verifying event markers in the EEG data to confirm all required events are accurately recorded.
- Ensuring the setup for stimulus presentation and EEG data acquisition adheres to the study protocol.
- Inspecting electrode impedances to ensure they are within acceptable limits.
- Detecting multiple task runs and incomplete recordings.
- Confirming the use of correct E-Prime task versions.

Both study sites and the EEG Core team use an EEG Quality Control dashboard developed by LORIS to access and monitor incoming EEG data and QC metrics, such as retained epochs and line noise levels. Outputs from the HBCD-Maryland Analysis of Developmental EEG ([HBCD-MADE](https://github.com/DCAN-Labs/HBCD-MADE)) pipeline, which handles preprocessing and data cleaning, are also integrated into the dashboard. These outputs include key metrics like outlier statistics for specific task epochs (Debnath et al., 2019). Regular site-specific check-ins and troubleshooting are conducted to ensure consistent protocol adherence and data quality across sites. For a detailed description of QC procedures in the HBCD Study EEG protocol, refer to [Fox et al. (2024)](https://doi.org/10.1016/j.dcn.2024.101447).

### Common QC & Potential Issues
During quality control, a frequently observed issue across all tasks was the irregular application of EEG sensors. Additionally, partial task completion due to infant fussing and missing stimulus flags were commonly noted for the faces and auditory mismatch negativity tasks.

Subject matter experts flagged potential issues related to task design changes between versions V03 and V04/6. These include updates to the video content in the video RS task and modifications to the interstimulus interval (ISI) in the auditory mismatch negativity task (see Fox et al., 2024; Morr et al., 2002, for details on the ISI changes). No potential issues were identified for the faces or visual evoked potential tasks.

## Resources
- [HBCD E-Prime Task Manual](pdfs/HBCDE-PrimeTaskManual.pdf)  
- [Official EEG Acquisition Manual](pdfs/OfficialEEGAcquisitionManual6.23.24.pdf)

