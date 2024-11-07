# MAPS-TL
## Measure Overview
**Full Name**: Multidimensional Assessment Profiles - Temper Loss scale.  
**Acronym/Brief Name**: MAPS-TL  
**Construct**: Irritability  

**Description**     
Multidimensional Assessment Profiles- Temper Loss scale (MAPS-TL) is a well-validated survey assessing irritability that serves as a tool for characterizing the developmental expression of early mental health risk. MAPS-TL measures a range of behaviors that encompass dysregulation, responsiveness to environmental input, and context. Questions inquire about the behaviors of the focal child over the past month. Irritability has been identified as an early dimensional marker of lifespan mental health risk. MAPS-TL aims to delineate the typical-to-atypical spectrum of irritability in early childhood and identify those young children at high probability of subsequent adaptational problems based on problems with dysregulation. 

**Scoring Description and Procedure**         
Each of the 17 items for MAPS-TL is answered on a scale of 1-6:  

>| Score | Description |
| - | - |
| 1 | Never |
| 2 | Rarely (Less than once per week) |
| 3 | Some (1-3) days of the week  |
| 4 | Most (4-6) days of the week  | 
| 5 | Every day of the week |
| 6 | Many times each day |

A **sum score** is generated when the caregiver provides a numerical score of 1 to 6 for at least 9 out of the 17 items. If fewer than 9 items are completed, the score is marked as missing. When responses are available for 9 to 16 items, a prorated score is calculated using the formula: `(sum of items answered / number of items answered) * 17`.

## Implementation & Data Collection
**Method of Administration**: This questionnaire is to be filled out by the child’s caregiver in a remote setting. Questions inquire about the behaviors of the focal child over the past month.  
**Spanish Translation**: Yes  
**Child Specific/Unspecific Form**: Child Specific  
**Respondent:** Primary Caregiver   
**Visits**: V03 (3-9 months)  
**Estimated length of time for completion**: 5 minutes 

## HBCD Modifications
<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Global Measure Changes</u></b></p>
Measure instructions and individuals items that reference gendered pronouns (‘his/hers’, ‘he/she’) were edited to either eliminate the pronouns entirely, or edited to replace gendered pronouns with ‘my child’ when eliminating pronouns was not grammatically possible. Items referencing “parent” were edited to “parent/caregiver.”

Because MAPS-TL psychometric validation was done using original MAPS-TL items, it is important that publications account for edits made to individual items as part of HBCD DEI review.

## Quality Control & Known Issues 
**QC Procedures**

 - Examine the range of the child’s age to ensure that it falls in the age range 3 to 9 months  
 - Examine missingness. Count the number of items answered for each participant  
 - Calculate sum scores and means applying our prorated scoring rule  
 - Generate summary statistics and visualizations for item-level frequencies, age, and scores  
 - Calculate Cronbach's Alpha for reliability  

**Common Issues Identified**    
Common QC issues included incorrect ages and prorated scoring not being applied to observations with missing responses.

**Potential Issues Flagged by Subject Matter Experts**      
The missingness rule not being correctly implemented leads to incorrect scores. Measure administration has a strict age cutoff. Age auto-generation needs to be fixed so that QC can ensure the measure is being administered to correct target population.

## References
- Krogh-Jespersen, S., Kaat, A. J., Petitclerc, A., Perlman, S. B., Briggs-Gowan, M. J., Burns, J. L., Adam, H., Nili, A., Gray, L., & Wakschlag, L. S. (2022). Calibrating temper loss severity in the transition to toddlerhood: Implications for developmental science. *Applied Developmental Science*, 26(4), 785–798. [https://doi.org/10.1080/10888691.2021.1995386](https://doi.org/10.1080/10888691.2021.1995386)