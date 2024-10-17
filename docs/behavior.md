# Behavior/Caregiver Child Interaction

## IBQ-R (VSF)+BI
The Infant Behavior Questionnaire-Revised (Very Short Form \+ BI) is designed to measure infant’s temperamental reactivity and regulation. The IBQ-R (VSF)+BI is adapted from the well validated IBQ-R Very Short Form, with additional items reflecting Behavioral Inhibition from the long form of the IBQ-R.

**Full Name**: Infant Behavior Questionnaire – Revised Very Short Form \+ Behavior Inhibition  
**Acronym/Brief Name**: IBQ  
**Construct**: Temperamental Surgency, Negative Affect, Effortful Control, and Behavioral Inhibition  
**Description**: The IBQ-R VSF is a caregiver report form used to assess temperament in infancy. Caregivers are asked to report on the infant’s behaviors on a 7-point Likert scale ranging from 1 (never) to 7 (always). For the purposes of HBCD, the measure consists of 4 scale domains: surgency (13 items), negative affect (12 items), effortful control (12 items), and behavioral inhibition (13 items).  
**Summary**: The IBQ provides a comprehensive assessment of early temperament, focusing on key traits that influence development and behavior during the early years.

### Publications and References 
Rothbart, M. K. (1981). Measurement of temperament in infancy. Child Development, 52, 569-578.

Gartstein, M. A., & Rothbart, M. K. (2003). Studying infant temperament via the Revised Infant Behavior Questionnaire. Infant Behavior and Development, 26 (1), 64-86.

Putnam, S. P., Helbig, A. L., Gartstein, M. A., Rothbart, M. K. & Leerkes, E. (2014). Development and Assessment of Short and Very Short Forms of the Infant Behavior Questionnaire-Revised. Journal of Personality Assessment, 96, 445-458.

### Implementation Details
**Method of Administration**: remote survey  
**REDCap Form Name**: mh\_cg\_ibqr  
**Pilot Data Dictionary**: IBQ  
**Spanish Translation**: Existing  
**Child Specific/Unspecific Form**: Child Specific  
**Respondent**: Caregiver

### Data Collection
**Visits Administered and corresponding age range of administration**: V03, V05, validated for ages 3 months 0 days to 17 months 30 days (for HBCD purposes)  
**Estimated length of time for completion**: Approximately 7-10 minutes     
**General Scoring Description and Procedure**:  
The IBQ-R+BI is scored in 4 domains: Surgency, Negative Affect, Effortful Control, Behavioral Inhibition. Respondents report on the frequency of infant’s behavior using the following scale:  

- 1 - Never
- 2 - Very rarely
- 3 - Less than half the time
- 4 - About half the time
- 5 - More than half the time
- 6 - Almost always
- 7 - Always
- 8 - (Does not apply/missing)  
   
Scale scores for the Infant Behavior Questionnaire – Revised – Very Short Form represent the mean score of all scale items applicable to the child, as judged by the caregiver. Scales' scores are to be computed by the following method:  
   
1. Sum all numerical item responses for a given scale. Note that:
- If caregiver omitted an item, that item receives no numerical score;
- If caregiver checked the "does not apply" or “choose not to respond” response option for an item, that item receives no numerical score;  
   
2. Divide the total by the number of items receiving a numerical response  
- Do not include items marked “does not apply (N/A)” or “choose not to respond” in determining the number of items.  
- If there are more than 40% of items from a scale missing (i.e., there are only 7/12 completed responses in a scale), it is not possible to score the individual domain.  
   
For example, given a sum of 47 for a scale of 12 items, with one item receiving no response, two items marked "does not apply," and 9 items receiving a numerical response, the sum of 47 would be divided by 9 to yield a mean of 5.22 for the scale score. Items with an “R” are reverse scored and already implemented in the HBCD scoring algorithm.

### Quality Control (QC) Processes
**QC Procedures**

- Examine the range of the child’s age to ensure that it falls in the age range 3 to 18 months
- Examine missingness. Count the number of items answered for each participant
- Calculate sum scores and means applying appropriate rules to account formissing data
- Generate summary statistics and visualizations for item-level frequencies, age, and scores
- Calculate Cronbach's Alpha for reliability  

**Common Issues Identified**:    
Scoring not accurately applied to observations with missing responses and incorrect administration ages, missing data patterns that may be site specific.

### Potential Issues Flagged by Subject Matter Experts

Subject matter experts identified no potential issues with IBQ

### Additional Information

[Mary Rothbart's Temperament Questionnaires](https://research.bowdoin.edu/rothbart-temperament-questionnaires)


## MAPS-TL
**Full Name**: Multidimensional Assessment Profiles \- Temper Loss scale.  
**Acronym/Brief Name**: MAPS-TL  
**Construct**: Irritability  
**Description**: Multidimensional Assessment Profiles- Temper Loss scale (MAPS-TL) is a well-validated survey assessing irritability that serves as a tool for characterizing the developmental expression of early mental health risk. MAPS-TL measures a range of behaviors that encompass dysregulation, responsiveness to environmental input, and context. Questions inquire about the behaviors of the focal child over the past month. Irritability has been identified as an early dimensional marker of lifespan mental health risk. MAPS-TL aims to delineate the typical:atypical spectrum of irritability in early childhood and identify those young children at high probability of subsequent adaptational problems based on problems with dysregulation. 

### Publications and References
Krogh-Jespersen, S., Kaat, A. J., Petitclerc, A., Perlman, S. B., Briggs-Gowan, M. J., Burns, J. L., ... & Wakschlag, L. S. (2022). Calibrating temper loss severity in the transition to toddlerhood: Implications for developmental science. *Applied developmental science,* 26(4), 785-798.

### Sum scores are computed by the following method:
1. If a caregiver answers all 17 items, sum all numerical item responses. All 17 raw items should be answered on a scale of 1:6:
- 1 - Never
- 2 - Rarely (Less than once per week)
- 3 - Some (1-3) days of the week   
* 4 - Most (4-6) days of the week   
* 5 - Every day of the week   
* 6 - Many times each day  

2. If a caregiver doesn’t answer an item (i.e., endorse any of the 6 options for an item), they get a missing value for that item. If a caregiver has missing data on some items but answers 9 items or more, then generate a prorated sum score. In other words: 
```
(Sum of items answered/the number of items answered)\*17
```

3. If a caregiver answers less than 9 items, then their sum score is missing

### Implementation Details
**Method of Administration**: This questionnaire is to be filled out by the child’s caregiver in a remote setting. Questions inquire about the behaviors of the focal child over the past month.  
**REDCap Form Name**: N/A  
**Pilot Data Dictionary**: N/A  
**Spanish Translation**: Yes  
**Child Specific/Unspecific Form**: Child Specific  
**Respondent:** Primary Caregiver

### Data Collection
**Visits Administered and corresponding age range of administration**: V03 age range; 3m 0 days– 9m 0 days  
**Estimated length of time for completion**: 5 minutes 

### Quality Control (QC) Processes
**QC Procedures**   
  * Examine the range of the child’s age to ensure that it falls in the age range 3 to 9 months  
  * Examine missingness. Count the number of items answered for each participant  
  * Calculate sum scores and means applying our prorated scoring rule  
  * Generate summary statistics and visualizations for item-level frequencies, age, and scores  
  * Calculate Cronbach's Alpha for reliability  

**Common Issues Identified**    
Prorated scoring not applied to observations with missing responses. Incorrect ages.

### Potential Issues Flagged by Subject Matter Experts

**MAPS-TL**: The missingness rule not being correctly implemented leads to incorrect scores. Measure administration has a strict age cutoff. Age auto-generation needs to be fixed so that QC can ensure the measure is being administered to correct target population.

## ecPROMIS Child-Caregiver Interaction
**Full Name**: Early Childhood Patient-Reported Outcome Measurement Information System Child/Caregiver Relationship Scale.
**Acronym/Brief Name**: ecPROMIS Child-Caregiver Interaction  
**Construct**: Relationships
**Description**: The Early Childhood Patient-Reported Outcome Measurement Information System (ecPROMIS) offers clinicians and researchers a brief, efficient, and precise way to evaluate young children’s well-being. The ecPROMIS Child-Caregiver Relationship Scale assesses the degree to which young children develop close, satisfying relationships with caregivers. Questions inquire about the focal child/caregiver relationship over the past 7 days. The ecPROMIS Child/Caregiver relationship form (Infancy: \< 1 year) was developed for HBCD based on the “PROMIS Early Childhood Parent-Report Short Form v1.0 \- Social Relationships – Child-Caregiver Interactions 5a” form.

### Publications and References
  Cella, D., Blackwell, C.K., & Wakschlag, L.S. (2022). Bringing PROMIS to Early Childhood: Introduction and Qualitative Methods for the Development of Early Childhood Parent Report Instruments. *Journal of Pediatric Psychology*, 47(5):500-9.

  Lai, J.S., Kallen, M.A., Blackwell, C.K., Wakschlag, L.S., & Cella, D. (2022). Psychometric Considerations in Developing PROMIS® Measures for Early Childhood. *Journal of Pediatric Psychology*, 47(5):510-22.

  Park, C.H., Blaisdell, C.J., & Gillman, M.W. (2022). The NIH ECHO Program: An Impetus for the Development of Early Childhood PROMIS Tools. *Journal of Pediatric Psychology*, 47(5), 497-499.

### Scoring Algorithms
Sum scores are computed by the following method:

  1\. If a caregiver answers all 5 items (‘fam\_ec2’, ‘fam\_ec6’, ‘fam\_ec1’, ‘fam\_ec4’, ‘fam\_ec10’), sum all numerical item responses.

  2\. If a caregiver doesn’t answer an item (i.e., endorse any of the 5 options for an item), they get a missing value for that item. If a caregiver has missing data on some items but answers 3 items or more, then generate a prorated sum score. In other words:

  (Sum of items answered/the number of items answered)\*5

  3\. If a caregiver answers less than 3 items, then their sum score is missing

  *(See Links to Resources*)

### Implementation Details
**Method of Administration**: This questionnaire is to be filled out by the child’s caregiver in a remote setting. 
**REDCap Form Name**: N/A
**Pilot Data Dictionary**: N/A
**Spanish Translation**: Yes
**Child Specific/Unspecific Form**: Child Specific
**Respondent:** Primary Caregiver

### Data Collection
**Visits Administered and corresponding age range of administration**: V03 age range; \<12mo age
**Estimated length of time for completion**: 1-2 minutes

### Quality Control (QC) Processes

**QC Procedures**   
  * Examine the range of the child’s age to ensure that it falls in the age range 3 to 9 months  
  * Examine missingness. Count the number of items answered for each participant  
  * Calculate sum scores and means applying our prorated scoring rule  
  * Generate summary statistics and visualizations for item-level frequencies, age, and scores  
  * Calculate Cronbach's Alpha for reliability  

**Common Issues Identified**  
Prorated scoring not applied to observations with missing responses. Incorrect ages.

### Potential Issues Flagged by Subject Matter Experts
**ecPROMIS**: The missingness rule not being correctly implemented leads to incorrect scores. Measure administration has a strict age cutoff. Age auto-generation needs to be fixed so that QC can ensure the measure is being administered to the correct target population.

### Additional Information
**Relevant Documents** 

  * HealthMeasures, the creators of ecPROMIS have an Assessment Center API that translates sum scores into T-scores (see Links to Resources). When administered in REDCap, sum scores can be auto-calculated, and trigger an API call to obtain corresponding T-scores. Higher T-scores represent more of the phenomenon being measured. In this case, higher T-scores indicate increased child/caregiver interaction. 

**Links to Resources** 

  * Assessment Center API: [https://www.healthmeasures.net/index.php?option=com\_content\&view=category\&layout=blog\&id=190\&Itemid=1214](https://www.healthmeasures.net/index.php?option=com_content&view=category&layout=blog&id=190&Itemid=1214)   