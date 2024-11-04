# ecPROMIS Child-Caregiver Interaction
## Measure Overview
**Full Name**: Early Childhood Patient-Reported Outcome Measurement Information System Child/Caregiver Relationship Scale.  
**Acronym/Brief Name**: ecPROMIS Child-Caregiver Interaction    
**Construct**: Relationships  

**Description**   
The Early Childhood Patient-Reported Outcome Measurement Information System (ecPROMIS) offers clinicians and researchers a brief, efficient, and precise way to evaluate young children’s well-being. The ecPROMIS Child-Caregiver Relationship Scale assesses the degree to which young children develop close, satisfying relationships with caregivers. Questions inquire about the focal child/caregiver relationship over the past 7 days. The ecPROMIS Child/Caregiver relationship form (Infancy: < 1 year) was developed for HBCD based on the “PROMIS Early Childhood Parent-Report Short Form v1.0 - Social Relationships – Child-Caregiver Interactions 5a” form.

**General Scoring Description and Procedure**   
A **sum score** is generated when the caregiver answers at least 3 out of the 5 items (`fam_ec2`, `fam_ec6`, `fam_ec1`, `fam_ec4`, `fam_ec10`). If caregivers answer 3 or 4 items, a prorated score is calculated using the formula: `(sum of items answered/the number of items answered)*5`. If fewer than 3 items are completed, the score is marked as missing. 

## Implementation & Data Collection
**Method of Administration**: This questionnaire is to be filled out by the child’s caregiver in a remote setting.    
**Spanish Translation**: Yes    
**Child Specific/Unspecific Form**: Child Specific    
**Respondent:** Primary Caregiver   
**Visits**: V03 (<12 months in age)  
**Estimated length of time for completion**: 1-2 minutes

## Quality Control & Known Issues
**QC Procedures**   

  * Examine the range of the child’s age to ensure that it falls in the age range 3 to 9 months  
  * Examine missingness. Count the number of items answered for each participant  
  * Calculate sum scores and means applying our prorated scoring rule  
  * Generate summary statistics and visualizations for item-level frequencies, age, and scores  
  * Calculate Cronbach's Alpha for reliability  

**Common Issues Identified**  
Common QC issues included incorrect ages and prorated scoring not being applied to observations with missing responses.

**Potential Issues Flagged by Subject Matter Experts**  
The missingness rule not being correctly implemented leads to incorrect scores. Measure administration has a strict age cutoff. Age auto-generation needs to be fixed so that QC can ensure the measure is being administered to the correct target population.

## Additional Information
HealthMeasures, the creators of ecPROMIS have an [Assessment Center API](https://www.healthmeasures.net/index.php?option=com_content&view=category&layout=blog&id=190&Itemid=1214) that translates sum scores into T-scores. When administered in REDCap, sum scores can be auto-calculated, and trigger an API call to obtain corresponding T-scores. Higher T-scores represent more of the phenomenon being measured. In this case, higher T-scores indicate increased child/caregiver interaction. 

## References
- Cella, D., Blackwell, C. K., & Wakschlag, L. S. (2022). Bringing PROMIS to Early Childhood: Introduction and qualitative methods for the development of Early Childhood Parent Report instruments. *Journal of Pediatric Psychology*, 47(5), 500–509. [https://doi.org/10.1093/jpepsy/jsac027](https://doi.org/10.1093/jpepsy/jsac027)
- Lai, J.-S., Kallen, M. A., Blackwell, C. K., Wakschlag, L. S., & Cella, D. (2022). Psychometric considerations in developing PROMIS® measures for early childhood. *Journal of Pediatric Psychology*, 47(5), 510–522. [https://doi.org/10.1093/jpepsy/jsac025](https://doi.org/10.1093/jpepsy/jsac025)
- Park, C. H., Blaisdell, C. J., & Gillman, M. W. (2022). The NIH ECHO program: An impetus for the development of early childhood PROMIS tools. *Journal of Pediatric Psychology*, 47(5), 497–499. [https://doi.org/10.1093/jpepsy/jsac010](https://doi.org/10.1093/jpepsy/jsac010)
