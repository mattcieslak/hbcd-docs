# Change Log / LORIS Data Release Beta: Current Version **BR5**/**v1.4**

## General Settings
**Destination S3 bucket:** hbcd-main-staging    
**Mounted Directory:** /loris/loris_server/volumes/data/loris/data/stg_s3_data/ 
**Data Structure:**
```
root_bids_directory 
└─── participants.tsv
└─── participants.json 
└─── assembly_bids
└─── phenotype  
    └─── visit_data.tsv
    └─── visit_data.json
    └─── sed_basic_demographics.tsv
    └─── sed_basic_demographics.json
    └─── biosample_urine.tsv 
    └─── biosample_urine.json
    └─── <instrument_name_1>.tsv *(Participant GUID & 'Visit Label' in first two columns)*    
    └─── <instrument_name_1>.json *(Instrument’s Data Dictionary)*
    └─── <instrument_name_2>.tsv   
    └─── <instrument_name_2>.json ...
```

**File Descriptions**
`participants.tsv`  > Participants list 
`participants.json` > Metadata for participants list    
`phenotype/`        > Folder containing instrument data table (.tsv) and Data Dictionary (.json) files  
`visit_data.tsv`    > Fields associated to visit level data     
`sed_basic_demographics.tsv` > Derived fields pertaining to demographic data 

**[Data Release Detailed settings](https://docs.google.com/spreadsheets/d/15Ne_q8-1dyTW3MWtUTfLp3nobRLIBaiYxV6k1_nL8EA/edit?gid=589752985#gid=589752985)**

**[HBCD - BIDS Descriptions for Data Release](datacuration/bids.md)**

## Version-Specific Settings & Implementations
### Version: **v1.4**
Total number of unique participants and visits included in first data dump:
* 1,367 unique participants  
* 1,919 visits  
  * V01 visits: 1,127 (185 participants for which only V01 visit exists)  
  * V02 visits: 666  
  * V03 visits: 126

#### New features
**Two new categories added to ‘phenotype’ folder with the following fields**   
‘*Basic Demographics*’ category:
    - Sex (*‘sex’*)  
    - Substance Use (*‘substance_use’*) (currently a placeholder)  
    - Child Race  
    - Child Ethnicity  
    - Maternal Race - Single Point  
    - Maternal Race - Multi  
    - Maternal Ethnicity  
    - Maternal Education  
    - Languages spoken at home  
    - Gestational age at birth (currently ‘n/a’ for all cases)  
    - Recruitment Site  

‘*Visit Data*’ category:  
    * Visit Label (*‘visit’*)  
    * Project (*‘project’*)  
    * Cohort (‘cohort’)  
    * Site (*‘site’*)  
    * Visit Stage (*‘visit_stage’*)  
    * Visit Date (*‘visit_date’*)  
    * Visit Missed (*visit_missed’*)  
    * Visit Missed - Reason (*‘reason_visit_missed’*)  
    * Participant Withdrawal (*‘participant_withdrawal’*)  
    * Participant Withdrawal - Reason (*‘participant_withdrawal_reason’*)  
    * Participant Withdrawal - Date (*‘participant_withdrawal_date’*)  
    * ProtocolException (*‘protocol_exception’*)  
    * Protocol Exception - Date (*‘protocol_exception_date’*)  

**Added new Data Dictionary elements (column headers)**   
  * Header (‘header’)  
  * Instruction ('instruction')  
  * Sort Order ('order_sort')  
  * Label in Spanish ('label_es')  
  * Instruction in Spanish ('instructions_es')  
  * Header in Spanish ('header_es')  
  * Note in Spanish ('note_es')  

**Relabeled Data Dictionary element**  
  *  ‘Full Instrument Name’ relabeled as ‘table_label’

#### Additional Filters
* Excluded GABI Setup/Receipt and all ERICA forms (Added to exclusion filter)

#### Data Conversions
Converted extreme values to ‘n/a’ as follows:  
  * Baby Birth Length data   
    * Instrument: *‘pex_bm_healthv2_inf’*  
    * Fields & Threshold (Anything above or below thresholds gets converted to 'n/a' - (Inclusive)):  
      * pex_bm_healthv2_inf_001_i_01 (Weight in Ounces)  
        * High: 16  
      * pex_bm_healthv2_inf_001_i_02 (Weight in Pounds)  
        * High: 66  
      * pex_bm_healthv2_inf_002 (Height/length in Inches)  
        * High: 51  
        * Low: 12  
      * pex_bm_healthv2_inf_002_i_01 (Height/length in cms)  
        * High: 130  
        * Low: 30

#### Previous Issues Addressed
* Import of ‘Maternal Demographic’ data from Ripple into LORIS

#### Additional Notes
* 'Site' included in phenotypical data under the new ‘*Visit Data*’ category (based on the 3 letter code; needs conversion to ‘HBCDsiteXX’ coding scheme)

### Version: **v1.3**
Total number of unique participants and visits included in first data dump: 
* 1,398 unique participants  
* 1,918 visits  
  * V01 visits: 1,126   
  * V02 visits: 666  
  * V03 visits: 126

#### New features
* Added 3 new Data Dictionary elements (column headers)   
  * Unit (‘unit’)  
  * Display order (‘order_display’)  
  * Note (‘note’)  
* Removed leaked HTML code from Data Dictionary and data

#### Additional Filters
Excluded 5 EUY participants: **TODO**

#### Data Conversions
* Converted 'Candidate age at Administration' from 'months' to 'years' (3 decimal point precision)  
* Converted 'DoB' and 'Candidate age at Administration' @ V01 to 'n/a'

#### Previous Issues Addressed
* Addressed participants listed on phenotype data but not listed in participants.tsv file (n=30)

#### Additional Notes
* 'Site' currently not included in phenotypical data, only on the scans.tsv  
* 'Site' to be added in future iterations as a column in each instrument's .csv file  
* Based on the 3 letter code, needs conversion to ‘HBCDsiteXX’ coding scheme

### Version: **v1.2**
Total number of unique participants and visits included in first data dump:
* 1,402 unique participants  
* 1,922 visits  
  * V01 visits: 1,126   
  * V02 visits: 669   
  * V03 visits: 127 
  
#### New features
* Added Data Dictionary elements (column headers) to accompanying json files  
* Added correct interpretation for html leak: ‘=&gt’ to ‘=>’

#### Data Conversions
* Data Dictionary column headers mapped to corresponding ABCD convention

#### Additional Notes
**Issues with Data Release:**
* 30 participants found in phenotypical data but not listed in participants.tsv file.

### Version: **v1.1**
#### New features
* USDTL Urine results embedded into 'Phenotype' folder as a .tsv

#### Additional Filters
* Additional 'Date of Administration' fields (dtt) excluded   
* Removal of PSCID column from `participant.tsv`

#### Data Conversions
* Fields with 'Null' converted to 'n/a' to align with BIDS compliance requirements  
* All field names converted to lowercase letters for BIDS compliance requirements

#### New Instruments or Data Added
* biosample_urine.json  
* biosample_urine.tsv

### Version: **v1.0**
Total number of unique participants and visits included in first data dump:   
* 1,406 unique participants  
* 1,939 visits  
  * V01 visits: 1,126   
  * V02 visits: 688   
  * V03 visits: 125 
