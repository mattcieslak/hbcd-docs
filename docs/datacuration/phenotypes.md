# Phenotypes Data Curation & BIDS Conversion

## Data Structure & File Contents

The data structure of the phenotypic data is as follows:
```
assembly_bids/ 
|__ participants.tsv
|__ participants.json 
|__ sub-<label>/
|   |__ sub-<label>_sessions.tsv
|   |__ sub-<label>_sessions.json
|   |__ ses-<label>/
|       |__ phenotype/
|       |   |__ biosample_urine.tsv
|       |   |__ biosample_urine.json
|       |   |__ sed_basic_demographics.tsv
|       |   |__ sed_basic_demographics.json
|       |   |__ visit_data.tsv
|       |   |__ visit_data.json
|       |   |__ <instrument_name>.tsv (repeat for all selected instruments)
|       |   |__ <instrument_name>.json (repeat for all selected instruments)
```

Below is additional information on the files and file contents provided for each phenotype:

<details>
<summary>Demographics files (<code>phenotype/sed_basic_demographics</code>)</summary>
<ul>
<br>
<i>These files contain demographics information including:</i>
    <li>Gestational age at birth</li>
    <li>Sex</li>
    <li>Recruitment site</li>
    <li>Child demographics: race, ethnicity</li>
    <li>Mother demographics: race, ethnicity, education, income, language spoken at home</li>
    <li>Substance Use (SU) - can be any of the following:
        <ul>
            <li>Self reported use (TLFB): any flag raised for SU</li>
            <li>Biospecimen: any result returning a flag for SU</li>
            <li>Health V2 instrument (‘pex_bm_healthv2_inf’): field “007”, option 1 (NOWS - Neonatal Opioid Withdrawal Syndrome) or 5 (FAS - Fetal Alcohol Syndrome) selected</li>
        </ul>
    </li>
</ul>
</details>

<details>
<summary>Biosample Urine Result files (<code>phenotype/biosample_urine</code>)</summary>
<ul>
<br>
<i>Regarding biosample urine result files:</i>
    <li>USDTL Urine results produced by BAH (Booz-Allen Hamilton)</li>
    <li>Includes DCCID, Visit Label, Scannable code, and other BioSpecimen result fields</li>
    <li>‘bio’ domain prepended for all protocol elements</li>
</ul>
</details>

<details>
<summary>Visit data files (<code>phenotype/visit_data</code>)</summary>
<ul>
<br>
<i>These files contain participant visit data including:</i>
    <li>Project</li>
    <li>Cohort</li>
    <li>Site</li>
    <li>Visit information:
         <ul>
            <li>Label</li>
            <li>Stage</li>
            <li>Date</li>
            <li>If the visit was missed and the reason</li>
         </ul>
    <li>Participant Withdrawal Information: If the participant withdrew from the study, the reason, and date</li>
    <li>Participant Protocol Exception Information: If there was a protocol exception, the type, and the date</li>
</ul>
</details>

<details>
<summary>Instrument data files (<code>phenotype/instrument_name</code>)</summary>
<ul>
<br>
<i>The following files are provided for each instrument:</i>
    <li><code><instrument_name>.tsv</code>: Data Table containing all instrument values for the participants</li>
    <li><code><instrument_name>.json</code>: Data Dictionary describing all instrument fields except those in the exclusion lists provided below</li>
</ul>
</details><br>




## Excluded Elements & General Rules
Below is a list of static elements (i.e. precisely identified hard-coded elements including participants, instruments, and instrument fields) and dynamic elements excluded during the data release process as well as general rules applied to all data:

<details>
<summary>Static Element Exclusions</summary>
<ul>
<br><i>Excluded Instruments</i>:
    <li>Biosensor Receipt Form ('sens_ch_rcpt')</li>
    <li>EEG Acquisition Form ('eeg_ch_chkl')</li>
    <li>EEG Acquisition Form Reattempt - 1 ('eeg_ch_chkl_1')</li>
    <li>EEG Acquisition Form Reattempt - 2 ('eeg_ch_chkl_2')</li>
    <li>MRI Data Summary Form ('mri_ra_chkl_data')</li>
    <li>MRI Scan Session Summary Form ('mri_ra_chkl_scan')</li>
    <li>MRI Pre/Post Scan Prep ('mri_ra_prep')</li>
    <li>NIH Baby ToolBox ('ncl_ch_nbtb')</li>
    <li>Participant Feedback Form ('adm_cg_fb')</li>
    <li>RA Feedback ('adm_ra_fb')</li>
    <li>Visit Level Data ('adm_fd_visitdata')</li>
    <li>Visit start ('visit_start')</li>
    <li>Urgent Events ('adm_fd_urgent')</li>
    <li>Participant Alerts ('admin_alert')</li>
    <li>TLFB (Timeline Follow Back) Summary Parser ('pex_ch_tlfb')</li>
    <li>Transitions in Care Questionnaire ('sed_cg_tic')</li>

<br><i>Excluded Instrument Fields (mostly metadata fields)</i>:
    <li>Date of Administration (‘date_taken’)</li>
    <li>Examiner (‘Examiner’)</li>
    <li>Timestamps ('timestamp', ‘timestamp_start', 'timestamp_stop', 'timestamp_start_tmp', 'timestamp_redcap_locked', 'dtt')</li>
    <li>REDCap Complete status ('complete')</li>
</ul>
</details>

<details>
<summary>Dynamic Element Exclusions</summary>
<ul>
    <li>No brain rating or brain rating noted “abnormal” are not selected</li>
    <li>Only active participants and sessions are selected</li>
    <li>Participants from Data Coordination Center (DCC) and University of Florida (UFL) sites are not selected</li>
    <li>Only participants with PSCIDs starting with “CH” are selected (excluding all test participants e.g. QI, YI, XI, PI)</li>
    <li>Participants having REDCap instruments not filled out by the exact “redcap” examiner will be excluded from the result (i.e. possible modification of data between REDCap and LORIS, or data entered directly into LORIS)</li>
    <li>For Beta Data Release, the process considers only data noted with launchpad complete status from before 2024-07-01 (YYYY-MM-DD)</li>
</ul>
</details>

<details>
<summary>General Rules Applied to All Data</summary>
<ul>
    <li>All participants having only one active visit that is V01 will have their sex changed to “Other” instead of “Male” or “Female”</li>
    <li>All empty string “” or missing values will be replaced with the default ReproSchema-compliant string “n/a”</li>
    <li>For V01, all “Candidate_Age” values are replaced with “n/a”</li>
    <li>For other visits, “Candidate_Age” will be computed in years</li>
    <li>Some fields can have out of range values. They are considered “extreme” values and are changed to “n/a”. Filters apply to:
        <ul>
            <li>Pex Bm Healthv2 Inf (‘pex_bm_healthv2_inf’) instrument:
                <ul>
                    <li>Field “001_i_01”: higher than 16</li>
                    <li>Field “001_i_02”: higher than 66</li>
                    <li>Field “002”: outside of range 12-51</li>
                    <li>Field “002_i_01”: outside of range 30-130</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
</details><br>
