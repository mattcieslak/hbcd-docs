# Instrument Data
The `phenotype/<instrument\_name\>` files contain `.tsv` tables per instrument with all instrument values for each participant. All fields for the instrument except those listed in the exclusion filter section below are included. The accompanying .json file for each instrument contains the Data Dictionary elements describing the instrument fields for the given instrument. 

# Basic Demographics
The `phenotype/sed_basic_demographics` files contain ‘Demographics’ data of general interest within the phenotype context, including:

* Sex  
* Recruitment site  
* Child Demographics  
  * Race  
  * Ethnicity  
* Mother demographics  
  * Race  
    Ethnicity  
  * Education  
  * Language spoken at home  
* Gestational age at birth (Not yet included/upcoming)  
* Substance Use (SU)  
  * Self reported use (TLFB)  
    * Flag raised for any SU category in TLFB  
  * BioSpecimen  
    * Any result returning a flag for SU  
  * Health V2 instrument (‘pex\_bm\_healthv2\_inf’)   
    * Neonatal Opioid Withdrawal Syndrome (NOWS) \- Field \-007’, option 1  
    * Fetal Alcohol Syndrome (FAS) \- Field ‘007’, option 5

# Visit Data
The `phenotype/visit_data` files contain all participant visit data. This includes:

* Project  
* Cohort  
* Site  
* Visit Information:  
  * Visit Label  
  * Visit Stage  
  * Visit Start Date  
  * Visit Missed  
  * Visit Missed \- Reason  
* Participant Withdrawal Information  
  * Participant Withdrawal  
  * Participant Withdrawal \- Reason  
  * Participant Withdrawal \- Date  
* Protocol Exception Information  
  * Protocol Exception  
  * Protocol Exception \- Type (Not yet added/Upcoming)  
  * Protocol Exception \- Date

# Biosample Urine
Regarding phenotype/biosample_urine files:

* USDTL Urine results   
* Updated up to July 1st  
* ‘bio’ domain prepended
