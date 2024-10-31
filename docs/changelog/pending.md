# Upcoming/Pending Updates

**Pending Field filters:**

* Brain Rating associated fields  
* Open text fields (Custom per instrument. Check on a case by case basis)  

**Upcoming**

* Change '_i_' to '__' in Data Dictionary  
* Gestational Age at Administration'  
* Optional Secondary Age for MRI 'scans.tsv'  
* scans.tsv file – MRI -  'Candidate Age at Administration' based on jittered DoB in ‘Years’ with three decimal point precision   
* scans.tsv file – EEG - 'Candidate Age at Administration' based on jittered DoB in ‘Years’ with three decimal point precision   
  
**Logs**

The following logs are generated for double-checking purposes (Logs are not shared nor embedded within the data dump structure):

* List of included participants (CandID/PSCID only)  
* List of included participants with 'Visit Label' (Same as above, with 'Visit Label')  
* Discrepancies in Participants queried from database vs the .tsv list of participants from assembly bids (based on the MRI pipeline)  
* Log of errors found during parsing of data release data dump

## Field Conversions [UNDER CONSTRUCTION]

* V01 conversions:  
  * The 'Sex' field for participants with only a V01 visit changed to 'Other'  
  * For V01, all “Candidate_Age” values are replaced with “n/a”  
* Empty string “” or missing values replaced with the default ReproSchema-compliant string “n/a”  
* 'Candidate age at Administration' converted from 'months' to 'years' with a 3 decimal point precision (for all visits other than V01)  
* Extreme/Out of range values converted to ‘n/a’. Current threshold conversions:  
  * Pex Bm Healthv2 Inf (‘pex_bm_healthv2_inf’) instrument:  
    * Field “001_i_01”: higher than 16.  
    * Field “001_i_02”: higher than 66.  
    * Field “002”: outside of range 12-51.  
    * Field “002_i_01”: outside of range 30-130.