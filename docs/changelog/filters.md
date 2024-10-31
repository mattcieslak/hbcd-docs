# Field Conversions

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

