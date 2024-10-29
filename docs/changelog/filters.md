# Dynamic Filters
This section lists **dynamic exclusions** applied during the Data Release process.

## Participant Filters
* DCC participants  
* Participant prefix (Included only 'CH' Participants):  
  * YI, XI, QI, PI  
* Participants from excluded sites  
  * University of Florida (FLU Participants)  
* Participants with ‘Brain Rating’:  
  * Abnormal  
    * 33 participants V02 'CH' participants)  
    * Differs from the numbers reported by Sauren (41 instances for V02 and 1 instance for V03). Follow-Up required by Chris & Jim (see 'Abnormal brain rating' email thread)

## Visit Filters
* Only visits whose 'LaunchPad Complete' Status was set to 'Complete' before July 1st, 2024 are included.

## Domain Filters
* BioSpecimens  
* Geocoding data  
* Transition in Care  
* REDCap surveys filled out directly in LORIS  
  * Identified based on LORIS 'Examiner' field not set to 'REDCap'

# Static Filters 
This section lists **static elements** excluded from the data release.

## Participant Filters
Based on Exclusion list ([HBCD - Data Release - Participants to Exclude](https://docs.google.com/spreadsheets/d/16jKl8BMqCFLqjXovIhzSUDJYh6lzT3ExPuVy6iUnV3E/edit?gid=0#gid=0)):  

  * Participants with a 'Postnatal Recruitment' visit  
  * Multiple Birth Participants

## Excluded Instruments
* BioSensor Receipt   
  * sens_ch_rcpt  
* EEG Acquisition Checklists  
  * eeg_ch_chkl  
  * eeg_ch_chkl_1  
  * eeg_ch_chkl_2  
* MRI Checklists  
  * mri_ra_chkl_data  
  * mri_ra_chkl_scan  
* MRI Pre/Post Scan Prep  
  * mri_ra_prep  
* NIH Baby Toolbox  
  * ncl_ch_nbtb  
* Participant Feedback  
  * adm_cg_fb  
* RA Feedback  
  * adm_ra_fb  
* Participant Alerts   
  * admin_alert  
* TLFB (Timeline Follow Back)   
  * pex_ch_tlfb  
* Transitions in Care Questionnaire   
  * sed_cg_tic  
* Visit Data  
  * adm_fd_visitdata  
* Visit Start  
  * visit_start  
* Urgent Events  
  * adm_fd_urgent

## Excluded instrument fields
* Examiner (Examiner)  
* Date of Birth (DOB)  
* Date of Administration (Date_taken)  
* Start timestamp (timestamp_start)  
* Stop timestamp (timestamp_stop)  
* REDCap timestamp (timestamp_redcap_locked)  
* Clinical Alerts  
* REDCap Complete status ('complete').  
* Scannable codes (BioSamples codes, tracking Nos, etc...)

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

# Upcoming/Pending Filters
## Pending Field filters
* Brain Rating associated fields  
* Open text fields (Custom per instrument. Check on a case by case basis)  
* Fields in 'HBCD_Include_vs_not_Include' tab of the '[Internal Facing](https://docs.google.com/spreadsheets/d/1qKuhIvogkOCVg-lDk30WKd5tfF0xuy-ChubOBSqOYNQ/edit?gid=1013027810#gid=1013027810)' document

## Upcoming
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

# Embedded instrument data files
These are the instruments/fields that were included in the release.

## V1.1
* biosample_urine.json  
* biosample_urine.tsv

## V1.0
* adm_bm_screen.json  
* adm_bm_screen.tsv  
* mh_cg_erica_3_7m.json  
* mh_cg_erica_3_7m.tsv  
* mh_cg_erica_7_9m.json  
* mh_cg_erica_7_9m.tsv  
* mh_cg_erica_cons_3_7m.json   
* mh_cg_erica_cons_3_7m.tsv  
* mh_cg_erica_cons_7_9m.json  
* mh_cg_erica_cons_7_9m.tsv  
* mh_cg_erica_fcm_3_7m.json  
* mh_cg_erica_fcm_3_7m.tsv  
* mh_cg_erica_fcm_7_9m.json  
* mh_cg_erica_fcm_7_9m.tsv  
* mh_cg_erica_fcm_adm_3_7m.json  
* mh_cg_erica_fcm_adm_3_7m.tsv  
* mh_cg_erica_fcm_adm_7_9m.json  
* mh_cg_erica_fcm_adm_7_9m.tsv  
* mh_cg_erica_rel_3_7m.json  
* mh_cg_erica_rel_3_7m.tsv  
* mh_cg_erica_rel_7_9m.json  
* mh_cg_erica_rel_7_9m.tsv  
* mh_cg_ibqr.json  
* mh_cg_ibqr.tsv  
* mh_cg_mapdb_i_inf.json  
* mh_cg_mapdb_i_inf.tsv  
* mh_cg_pms_i_cc_i_inf.json  
* mh_cg_pms_i_cc_i_inf.tsv  
* ncl_cg_spm2_i_inf.json  
* ncl_cg_spm2_i_inf.tsv  
* ncl_ch_mlds.json  
* ncl_ch_mlds.tsv  
* nt_ch_sens_i_qtn_1.json  
* nt_ch_sens_i_qtn_1.tsv  
* nt_ch_sens_i_qtn_2.json  
* nt_ch_sens_i_qtn_2.tsv  
* nt_ch_sens_i_qtn_3.json  
* nt_ch_sens_i_qtn_3.tsv  
* nt_pa_gabi_rcpt.json  
* nt_pa_gabi_rcpt.tsv  
* nt_pa_gabi_setup.json  
* nt_pa_gabi_setup.tsv  
* pex_bm_apa.json  
* pex_bm_apa.tsv  
* pex_bm_assistv1.json  
* pex_bm_assistv1.tsv  
* pex_bm_assistv2.json  
* pex_bm_assistv2.tsv  
* pex_bm_assistv3.json  
* pex_bm_assistv3.tsv  
* pex_bm_epds.json  
* pex_bm_epds.tsv  
* pex_bm_health_preg_i_chroncond.json  
* pex_bm_health_preg_i_chroncond.tsv  
* pex_bm_health_preg_i_erhosp.json  
* pex_bm_health_preg_i_erhosp.tsv  
* pex_bm_health_preg_i_exp_i_vacc.json  
* pex_bm_health_preg_i_exp_i_vacc.tsv  
* pex_bm_health_preg_i_healthhx.json  
* pex_bm_health_preg_i_healthhx.tsv  
* pex_bm_health_preg_i_illness.json  
* pex_bm_health_preg_i_illness.tsv  
* pex_bm_health_preg_i_meds.json  
* pex_bm_health_preg_i_meds.tsv  
* pex_bm_healthv2_inf.json  
* pex_bm_healthv2_inf.tsv  
* pex_bm_healthv2_preg.json  
* pex_bm_healthv2_preg.tsv  
* pex_bm_psych.json  
* pex_bm_psych.tsv  
* pex_bm_str_i_ptsd.json  
* pex_bm_str_i_ptsd.tsv  
* ph_cg_phx_i_bfh.json  
* ph_cg_phx_i_bfh.tsv  
* ph_ch_anthro.json  
* ph_ch_anthro.tsv  
* sed_bm_bfy.json  
* sed_bm_bfy.tsv  
* sed_bm_demo.json  
* sed_bm_demo.tsv  
* sed_bm_ehits.json  
* sed_bm_ehits.tsv  
* sed_bm_nbhsaf.json  
* sed_bm_nbhsaf.tsv  
* sed_bm_paces.json  
* sed_bm_paces.tsv  
* sed_bm_phx_i_discr.json  
* sed_bm_phx_i_discr.tsv  
* sed_bm_strsup.json  
* sed_bm_strsup.tsv  
* sed_cg_foodins.json  
* sed_cg_foodins.tsv  
* sens_ch_setup.json  
* sens_ch_setup.tsv