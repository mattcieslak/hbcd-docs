# Dynamic Filters
This section lists **dynamic exclusions** applied during the Data Release process.

**Participant filters:**

* DCC participants  
* Participant prefix (Included only 'CH' Participants):  
  * YI, XI, QI, PI  
* Participants from excluded sites  
  * University of Florida (FLU Participants)  
* Participants with ‘Brain Rating’:  
  * Abnormal  
    * 33 participants V02 'CH' participants)  
    * Differs from the numbers reported by Sauren (41 instances for V02 and 1 instance for V03). Follow-Up required by Chris & Jim (see 'Abnormal brain rating' email thread)

**Visit filters:**

* Only visits whose 'LaunchPad Complete' Status was set to 'Complete' before July 1st, 2024 are included.

**Domain filters:**

* BioSpecimens  
* Geocoding data  
* Transition in Care  
* REDCap surveys filled out directly in LORIS  
  * Identified based on LORIS 'Examiner' field not set to 'REDCap'

# Explicitly excluded elements in phenotype data
This section lists **static elements** excluded from the data release.

**Participant filters:**

* Based on Exclusion list ([HBCD \- Data Release - Participants to Exclude](https://docs.google.com/spreadsheets/d/16jKl8BMqCFLqjXovIhzSUDJYh6lzT3ExPuVy6iUnV3E/edit?gid=0#gid=0)):  
  * Participants with a 'Postnatal Recruitment' visit  
  * Multiple Birth Participants

**Excluded Instruments**:

* BioSensor Receipt   
  * sens\_ch\_rcpt  
* EEG Acquisition Checklists  
  * eeg\_ch\_chkl  
  * eeg\_ch\_chkl\_1  
  * eeg\_ch\_chkl\_2  
* MRI Checklists  
  * mri\_ra\_chkl\_data  
  * mri\_ra\_chkl\_scan  
* MRI Pre/Post Scan Prep  
  * mri\_ra\_prep  
* NIH Baby Toolbox  
  * ncl\_ch\_nbtb  
* Participant Feedback  
  * adm\_cg\_fb  
* RA Feedback  
  * adm\_ra\_fb  
* Participant Alerts   
  * admin\_alert  
* TLFB (Timeline Follow Back)   
  * pex\_ch\_tlfb  
* Transitions in Care Questionnaire   
  * sed\_cg\_tic  
* Visit Data  
  * adm\_fd\_visitdata  
* Visit Start  
  * visit\_start  
* Urgent Events  
  * adm\_fd\_urgent

**Excluded instrument fields:**

* Examiner (Examiner)  
* Date of Birth (DOB)  
* Date of Administration (Date\_taken)  
* Start timestamp (timestamp\_start)  
* Stop timestamp (timestamp\_stop)  
* REDCap timestamp (timestamp\_redcap\_locked)  
* Clinical Alerts  
* REDCap Complete status ('complete').  
* Scannable codes (BioSamples codes, tracking Nos, etc...)

**Field Conversions**

* V01 conversions:  
  * The 'Sex' field for participants with only a V01 visit changed to 'Other'  
  * For V01, all “Candidate\_Age” values are replaced with “n/a”  
* Empty string “” or missing values replaced with the default ReproSchema-compliant string “n/a”  
* 'Candidate age at Administration' converted from 'months' to 'years' with a 3 decimal point precision (for all visits other than V01)  
* Extreme/Out of range values converted to ‘n/a’. Current threshold conversions:  
  * Pex Bm Healthv2 Inf (‘pex\_bm\_healthv2\_inf’) instrument:  
    * Field “001\_i\_01”: higher than 16\.  
    * Field “001\_i\_02”: higher than 66\.  
    * Field “002”: outside of range 12-51.  
    * Field “002\_i\_01”: outside of range 30-130.

# Upcoming/Pending Filters
**Pending Field filters:**

* Brain Rating associated fields  
* Open text fields (Custom per instrument. Check on a case by case basis)  
* Fields in 'HBCD\_Include\_vs\_not\_Include' tab of the '[Internal Facing](https://docs.google.com/spreadsheets/d/1qKuhIvogkOCVg-lDk30WKd5tfF0xuy-ChubOBSqOYNQ/edit?gid=1013027810#gid=1013027810)' document

**Upcoming:**

* Change '\_i\_' to '\_\_' in Data Dictionary  
* Gestational Age at Administration'  
* Optional Secondary Age for MRI 'scans.tsv'  
* scans.tsv file – MRI \-  'Candidate Age at Administration' based on jittered DoB in ‘Years’ with three decimal point precision   
* scans.tsv file – EEG \- 'Candidate Age at Administration' based on jittered DoB in ‘Years’ with three decimal point precision   
  
**Logs**

The following logs are generated for double-checking purposes (Logs are not shared nor embedded within the data dump structure):

* List of included participants (CandID/PSCID only)  
* List of included participants with 'Visit Label' (Same as above, with 'Visit Label')  
* Discrepancies in Participants queried from database vs the .tsv list of participants from assembly bids (based on the MRI pipeline)  
* Log of errors found during parsing of data release data dump

**Embedded instrument data files**

These are the instruments/fields that were included in the release.

**V1.1:**

* biosample\_urine.json  
* biosample\_urine.tsv

**V1.0:**

* adm\_bm\_screen.json  
* adm\_bm\_screen.tsv  
* mh\_cg\_erica\_3\_7m.json  
* mh\_cg\_erica\_3\_7m.tsv  
* mh\_cg\_erica\_7\_9m.json  
* mh\_cg\_erica\_7\_9m.tsv  
* mh\_cg\_erica\_cons\_3\_7m.json   
* mh\_cg\_erica\_cons\_3\_7m.tsv  
* mh\_cg\_erica\_cons\_7\_9m.json  
* mh\_cg\_erica\_cons\_7\_9m.tsv  
* mh\_cg\_erica\_fcm\_3\_7m.json  
* mh\_cg\_erica\_fcm\_3\_7m.tsv  
* mh\_cg\_erica\_fcm\_7\_9m.json  
* mh\_cg\_erica\_fcm\_7\_9m.tsv  
* mh\_cg\_erica\_fcm\_adm\_3\_7m.json  
* mh\_cg\_erica\_fcm\_adm\_3\_7m.tsv  
* mh\_cg\_erica\_fcm\_adm\_7\_9m.json  
* mh\_cg\_erica\_fcm\_adm\_7\_9m.tsv  
* mh\_cg\_erica\_rel\_3\_7m.json  
* mh\_cg\_erica\_rel\_3\_7m.tsv  
* mh\_cg\_erica\_rel\_7\_9m.json  
* mh\_cg\_erica\_rel\_7\_9m.tsv  
* mh\_cg\_ibqr.json  
* mh\_cg\_ibqr.tsv  
* mh\_cg\_mapdb\_i\_inf.json  
* mh\_cg\_mapdb\_i\_inf.tsv  
* mh\_cg\_pms\_i\_cc\_i\_inf.json  
* mh\_cg\_pms\_i\_cc\_i\_inf.tsv  
* ncl\_cg\_spm2\_i\_inf.json  
* ncl\_cg\_spm2\_i\_inf.tsv  
* ncl\_ch\_mlds.json  
* ncl\_ch\_mlds.tsv  
* nt\_ch\_sens\_i\_qtn\_1.json  
* nt\_ch\_sens\_i\_qtn\_1.tsv  
* nt\_ch\_sens\_i\_qtn\_2.json  
* nt\_ch\_sens\_i\_qtn\_2.tsv  
* nt\_ch\_sens\_i\_qtn\_3.json  
* nt\_ch\_sens\_i\_qtn\_3.tsv  
* nt\_pa\_gabi\_rcpt.json  
* nt\_pa\_gabi\_rcpt.tsv  
* nt\_pa\_gabi\_setup.json  
* nt\_pa\_gabi\_setup.tsv  
* pex\_bm\_apa.json  
* pex\_bm\_apa.tsv  
* pex\_bm\_assistv1.json  
* pex\_bm\_assistv1.tsv  
* pex\_bm\_assistv2.json  
* pex\_bm\_assistv2.tsv  
* pex\_bm\_assistv3.json  
* pex\_bm\_assistv3.tsv  
* pex\_bm\_epds.json  
* pex\_bm\_epds.tsv  
* pex\_bm\_health\_preg\_i\_chroncond.json  
* pex\_bm\_health\_preg\_i\_chroncond.tsv  
* pex\_bm\_health\_preg\_i\_erhosp.json  
* pex\_bm\_health\_preg\_i\_erhosp.tsv  
* pex\_bm\_health\_preg\_i\_exp\_i\_vacc.json  
* pex\_bm\_health\_preg\_i\_exp\_i\_vacc.tsv  
* pex\_bm\_health\_preg\_i\_healthhx.json  
* pex\_bm\_health\_preg\_i\_healthhx.tsv  
* pex\_bm\_health\_preg\_i\_illness.json  
* pex\_bm\_health\_preg\_i\_illness.tsv  
* pex\_bm\_health\_preg\_i\_meds.json  
* pex\_bm\_health\_preg\_i\_meds.tsv  
* pex\_bm\_healthv2\_inf.json  
* pex\_bm\_healthv2\_inf.tsv  
* pex\_bm\_healthv2\_preg.json  
* pex\_bm\_healthv2\_preg.tsv  
* pex\_bm\_psych.json  
* pex\_bm\_psych.tsv  
* pex\_bm\_str\_i\_ptsd.json  
* pex\_bm\_str\_i\_ptsd.tsv  
* ph\_cg\_phx\_i\_bfh.json  
* ph\_cg\_phx\_i\_bfh.tsv  
* ph\_ch\_anthro.json  
* ph\_ch\_anthro.tsv  
* sed\_bm\_bfy.json  
* sed\_bm\_bfy.tsv  
* sed\_bm\_demo.json  
* sed\_bm\_demo.tsv  
* sed\_bm\_ehits.json  
* sed\_bm\_ehits.tsv  
* sed\_bm\_nbhsaf.json  
* sed\_bm\_nbhsaf.tsv  
* sed\_bm\_paces.json  
* sed\_bm\_paces.tsv  
* sed\_bm\_phx\_i\_discr.json  
* sed\_bm\_phx\_i\_discr.tsv  
* sed\_bm\_strsup.json  
* sed\_bm\_strsup.tsv  
* sed\_cg\_foodins.json  
* sed\_cg\_foodins.tsv  
* sens\_ch\_setup.json  
* sens\_ch\_setup.tsv