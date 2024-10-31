# Phenotypes Data Curation & BIDS Conversion

## Data Structure
```
root/
|__ assembly_bids/
|__ participants.tsv
|__ participants.json
|__ phenotype/
|   |__ biosample_urine.tsv
|   |__ biosample_urine.json
|   |__ sed_basic_demographics.tsv
|   |__ sed_basic_demographics.json
|   |__ visit_data.tsv
|   |__ visit_data.json
|   |__ <instrument_name>.tsv (repeat for all selected instruments)
|   |__ <instrument_name>.json (repeat for all selected instruments)
```

**Instrument Data**
The `phenotype/<instrument_name>` files contain `.tsv` tables per instrument with all instrument values for each participant. All fields for the instrument except those listed in the exclusion filter section are included. The accompanying .json file for each instrument contains the Data Dictionary elements describing the instrument fields for the given instrument. 

## Excluded Elements
### Static Elements Excluded
Excluded **participants**:

- ARK: 2  
- BCH: 1  
- CCH: 2  
- EUY: 6  
- JHU: 2  
- NWU: 1  
- NYU: 1  
- OHS: 4  
- PHI: 1  
- UCS: 1  
- UMN: 2  
- UNM: 1  
- UVM: 2  
- VAN: 1  
- WIS: 1  
- PUP: 1

Excluded **instruments**:

- Biosensor Receipt Form ('sens_ch_rcpt')  
- EEG Acquisition Form ('eeg_ch_chkl')  
- EEG Acquisition Form Reattempt - 1 ('eeg_ch_chkl_1')  
- EEG Acquisition Form Reattempt - 2 ('eeg_ch_chkl_2')  
- MRI Data Summary Form ('mri_ra_chkl_data')  
- MRI Scan Session Summary Form ('mri_ra_chkl_scan')  
- Pre/Post Scan Prep ('mri_ra_prep')  
- NIH Baby ToolBox ('ncl_ch_nbtb')  
- Participant Feedback Form ('adm_cg_fb')  
- RA Feedback ('adm_ra_fb')  
- Visit Level Data ('adm_fd_visitdata’)  
- Visit start ('visit_start')  
- Urgent Events ('adm_fd_urgent')  
- Participant Alerts ('admin_alert')  
- TLFB (Timeline Follow Back) Summary Parser ('pex_ch_tlfb')  
- Transitions in Care Questionnaire ('sed_cg_tic')

Excluded **instrument fields**, mostly metadata fields:

- Date of Administration (‘date_taken’).  
- Examiner (‘Examiner’).  
- Timestamps ('timestamp', ‘timestamp_start', 'timestamp_stop', 'timestamp_start_tmp', 'timestamp_redcap_locked', 'dtt').  
- REDCap Complete status ('complete').

### Dynamic Elements Excluded

- No brain rating or brain rating noted “abnormal” are not selected  
- Only active participants and sessions are selected  
- For Beta Data Release, the process considers only data noted with launchpad complete status from before 2024-07-01 (YYYY-MM-DD)  
- Participants from Data Coordination Center (DCC) and University of Florida (UFL) sites are not selected  
- Only participants with PSCIDs starting with “CH” are selected (excluding all test participants e.g. QI,YI,XI)  
- Participants having REDCap instruments not filled out by the exact “redcap” examiner will be excluded from the result (i.e. possible modification of data between REDCap and LORIS, or data entered directly into LORIS)

### General Rules Applied to All Data

- All participants having only one active visit that is V01 will have their sex changed to “Other” instead of “Male” or “Female”  
- All empty string “” or missing values will be replaced with the default ReproSchema-compliant string “n/a”  
- For V01, all “Candidate_Age” values are replaced with “n/a”  
- For other visits, “Candidate_Age” will be computed in years  
- Some fields can have out of range values. They are considered “extreme” values and are changed to “n/a”. Filters apply to:  
   - Pex Bm Healthv2 Inf (‘pex_bm_healthv2_inf’) instrument:  
      - Field “001_i_01”: higher than 16  
      - Field “001_i_02”: higher than 66  
      - Field “002”: outside of range 12-51  
      - Field “002_i_01”: outside of range 30-130

## Biosample Urine Results
Regarding `phenotype/biosample_urine` files:

- USDTL Urine results   
- Updated up to July 1st  
- File produced by BAH  
- Includes DCCID, Visit Label & Scannable code  
- ‘bio’ domain prepended

## Basic Demographics
The `phenotype/sed_basic_demographics` files contain demographics data of each participant useful with phenotype context, including:

- Gestational age at birth  
- Sex  
- Recruitment site  
- Child demographics: race, ethnicity  
- Mother demographics: race, ethnicity, education, income, language at home  
- Substance Use (SU) - can be any of the following:  
  - TLFB instrument: any flag raised for SU  
  - Biospecimen: any result returning a flag for SU  
  - Health V2 instrument (‘pex_bm_healthv2_inf’): field “007”, option 1 (NOWS - Neonatal Opioid Withdrawal Syndrome) or 5 (FAS - Fetal Alcohol Syndrome) selected

## Visit Data
The `phenotype/visit_data` files contain all participant visit data. This includes:

- Visit information:  
   - Label  
   - Stage  
   - Date  
   - If the visit was missed and the reason  
- Project  
- Cohort  
- Site  
- Withdrawal info: If the participant withdrew from the study, the reason and date  
- Protocol violation: If there was a protocol exception and the date

## Instrument Data
Regarding `phenotype/<instrument_name>` files, they contain all instrument answers of each participant split by instrument. Each file contains their full respective set of fields, depending on the instrument, minus the excluded fields mentioned above.
