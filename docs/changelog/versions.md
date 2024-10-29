LORIS Data Release Beta: Current Version **BR5**/**v1.4**
# Version-Specific Settings & Implementations

## Version: v1.2
Total number of unique participants and visits included in first data dump:
* 1,402 unique participants  
* 1,922 visits  
  * V01 visits: 1,126   
  * V02 visits: 669   
  * V03 visits: 127 
  
### New features
* Added Data Dictionary elements (column headers) to accompanying json files  
* Added correct interpretation for html leak: ‘=&gt’ to ‘=>’

### Data Conversions
* Data Dictionary column headers mapped to corresponding ABCD convention

### Additional Notes
**Issues with Data Release:**
* 30 participants found in phenotypical data but not listed in participants.tsv file.

## Version: v1.1
### New features
* USDTL Urine results embedded into 'Phenotype' folder as a .tsv

### Additional Filters
* Additional 'Date of Administration' fields (dtt) excluded   
* Removal of PSCID column from `participant.tsv`

### Data Conversions
* Fields with 'Null' converted to 'n/a' to align with BIDS compliance requirements  
* All field names converted to lowercase letters for BIDS compliance requirements

### New Instruments or Data Added
* biosample_urine.json  
* biosample_urine.tsv

## Version: **v1.0**
Total number of unique participants and visits included in first data dump:   
* 1,406 unique participants  
* 1,939 visits  
  * V01 visits: 1,126   
  * V02 visits: 688   
  * V03 visits: 125 
