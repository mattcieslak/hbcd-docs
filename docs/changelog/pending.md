# Pending & Upcoming Updates

## Pending Field Filters

* Brain Rating associated fields  
* Open text fields (Custom per instrument. Check on a case by case basis)  

## Upcoming Updates

* Change `_i_` to `__` in Data Dictionary  
* `Gestational Age at Administration`  
* Optional Secondary Age for MRI `scans.tsv`  
* `scans.tsv` file - MRI -  `Candidate Age at Administration` based on jittered DoB in `Years` with three decimal point precision   
* `scans.tsv` file – EEG - `Candidate Age at Administration` based on jittered DoB in `Years` with three decimal point precision   
  
## Logs

The following logs are generated for double-checking purposes (Logs are not shared nor embedded within the data dump structure):

* List of included participants (CandID/PSCID only)  
* List of included participants with `Visit Label` (Same as above, with `Visit Label`)  
* Discrepancies in Participants queried from database vs the `.tsv` list of participants from assembly bids (based on the MRI pipeline)  
* Log of errors found during parsing of data release data dump