# Pregnancy Health Measures
## Pregnancy Health
**Acronym/Brief Name**: Healthhx  
**Construct**: Pre-pregnancy and pregnancy health  
**Description**: This was a created to assess pre-pregnancy and pregnancy health  
**Summary**: Gravidity and parity, height and weight, pregnancy intentions, use of assisted reproductive technology, start of prenatal care, prenatal vitamin or aspirin use, secondhand smoke.

## Pregnancy Health- Vaccines  
**Acronym/Brief Name**: Exp I vacc  
**Construct**: Vaccines in pregnancy  
**Description**: This was a created to assess vaccine receipt in pregnancy  
**Summary**: Asks about receipt of a list of common vaccines in pregnancy, and trimester received

## Pregnancy Health- Chronic Conditions  
**Acronym/Brief Name**: Exp I chroncond  
**Construct**: chronic conditions and sexually transmitted infections in pregnancy  
**Description**: This was a created to capture chronic conditions (queried from a list) and sexually transmitted diseases in pregnancy.   
**Summary**: Asks about a pre-defined list of chronic conditions and sexually transmitted infections in pregnancy. Endorsed chronic conditions are asked whether they are ongoing or resolved. 

## Pregnancy Health - Illness  
**Acronym/Brief Name**: Exp I illness  
**Construct**: Illness in pregnancy  
**Description**: This was a created to capture illnesses in pregnancy  
**Summary**: Asks about covid-19 or other illnesses in pregnancy, including start and stop dates and whether the person had a fever.    

## Pregnancy Health- ER/Hospitalizations  
**Acronym/Brief Name**: Exp I ERhosp  
**Construct**: ER visit or hospitalization in pregnancy  
**Description**: This was a created to capture reasons for any ER visits or hospitalizations in pregnancy  
**Summary**: Asks about any ER visits or hospitalizations in pregnancy      

## Pregnancy Health- Medications  
**Acronym/Brief Name**: Exp I Meds  
**Construct**: prescription and over the counter medications in pregnancy  
**Description**: This was a created to capture prescription and over the counter medications in pregnancy.  
**Summary**: Asks about any prescription or over the counter medications used since last menstrual period. For each, the participant is asked medication name, indication, frequency, start and stop date (if applicable).      

## Pregnancy Health- V2 (End of Pregnancy) 
**Acronym/Brief Name**: Healthv2 Preg  
**Construct**: updates information between enrollment and delivery  
**Description**: This was a created to capture exposures between enrollment and delivery  
**Summary**: Updates information on prenatal vitamins, aspirin, infections, vaccines, prescription and over the counter medications (both continued from V1 and any new medications) and illnesses. In addition, we ask about pregnancy complications (from a list: e.g. gestational diabetes), labor, mode of delivery, place of delivery, and how many nights the birthing person remained in the hospital.   

## SUMMARY: Implementation & Known Issues
### Implementation & Data Collection
***Implementation parameters consistent across all pregnancy health measures***:       
**Spanish Translation**: Created  
**Child Specific/Unspecific Form**: Unspecific  
**Respondent**: Pregnant Person         

***Measure-specific implementation & data collection parameters***:

| Measure | REDCap Name | Administration Method | Time | Visit |
| - | - | - | - | - |
| Pregnancy Health | `Healthhx` | self-administered | 5 min | V1* |
| PH-Vaccines | `Vacc` | self-administered  | 3 min | V1* |
| PH-Chronic Conditions | `chroncond` | self-administered | 3 min | V1* |
| PH-Illness | `illness` | RA-administered | 3 min | V1* |
| PH-ER/Hospitalizations | `ERhosp` | RA-administered | 5 min | V1* |
| PH-Medications | `Meds`| RA-administered | 5 min | V1* |
| PH-V2 (End of Pregnancy) | `HealthV2 Preg` | RA-administered | 10 min | V2* |

<sup>* V1 visits occurred during pregnancy and V2 occurred 0-1 months postnatal</sup> 

### Known Issues 
**PH - Illness**    
Illnesses are captured either from ICD codes (from BioPortal ICD) or symptom codes (from World Health Organization), which were at times difficult for the participant to name or the RA to correctly find in the ICD or symptom database.

**PH - ER/Hospitalizations**    
Reasons for ER visit or hospitalization are captured from ICD codes (from BioPortal ICD), which were at times difficult for the participant to name or the RA to correctly find in the ICD database. This was particularly apparent for use of the ER for normal care (no diagnosis) or false alarms (e.g. thought water broke but it did not), resulting in the use of ‘don’t know.’

**PH - Medications**     
Medication was queried from the RxNORM database. Reasons for medication use are captured from ICD codes (from BioPortal ICD), which were at times difficult for the participant to name or the RA to correctly find in the ICD database. This was apparent with aspirin used for preeclampsia, as there was not an option for coding preventive use. Aspirin was specifically moved to the prenatal vitamin section a few months into the study. Additionally, medications used PRN were difficult for the participant to report. Finally, although not asked, some medications were coded with the dose in the database, although this was not asked and should not be used.

**PH - V2 (End of Pregnancy)**  
Same issues identified at V1 (difficulty with ICD codes (from BioPortal ICD) and medication names (from RxNORM)) apply to this visit as well.


