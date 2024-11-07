# IBQ-R (VSF)+BI
## Measure Overview
**Full Name**: Infant Behavior Questionnaire – Revised Very Short Form + Behavior Inhibition  
**Acronym/Brief Name**: IBQ  
**Construct**: Temperamental Surgency, Negative Affect, Effortful Control, and Behavioral Inhibition  

**Description**   
The IBQ-R VSF is a caregiver report form used to assess temperamental reactivity and regulation in infancy. It is adapted from the well validated IBQ-R Very Short Form, with additional items reflecting Behavioral Inhibition from the long form of the IBQ-R. Caregivers are asked to report on the infant’s behaviors on a 7-point Likert scale ranging from 1 (never) to 7 (always). For the purposes of HBCD, the measure consists of 4 scale domains: surgency (13 items), negative affect (12 items), effortful control (12 items), and behavioral inhibition (13 items).  

**Scoring Description and Procedure**     
The IBQ-R+BI is scored in 4 domains: Surgency, Negative Affect, Effortful Control, and Behavioral Inhibition. Respondents report on the frequency of their infant’s behavior using the following scale: 

>| Score | Description |
| - | - |
| 1 | Never |
| 2 | Very rarely |
| 3 | Less than half the time |
| 4 | About half the time | 
| 5 | More than half the time |
| 6 | Almost always |
| 7 | Always |

Scale scores generated for each domain are the mean score of all scale items applicable to the child as judged by the caregiver (`sum of item scores / total # of items` per domain). Importantly, this calculation only includes items with scores of 1 through 7: items where the caregiver selects "does not apply" or “choose not to respond" receive no numerical score and are not included in the total number of items for the scale. Items with an “R” are reverse scored and already implemented in the HBCD scoring algorithm.

**Summary**   
The IBQ provides a comprehensive assessment of early temperament, focusing on key traits that influence development and behavior during the early years.

## Implementation & Data Collection
**Method of Administration**: remote survey  
**REDCap Form Name**: `mh_cg_ibqr`    
**Pilot Data Dictionary**: IBQ  
**Spanish Translation**: Existing  
**Child Specific/Unspecific Form**: Child Specific  
**Respondent**: Caregiver   
**Visits**: V03, V05, validated for ages 3 months 0 days to 17 months 30 days (for HBCD purposes)  
**Estimated length of time for completion**: Approximately 7-10 minutes     

## HBCD Modifications
<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Global Measure Changes</u></b></p>
Alterations were made to items when the item referred to the child/baby as “s/he” or “her/him”. These pronouns were changed to “the baby/child,” “they/them” as fit the item wording. In addition, “Parent” was changed to “parent/caregiver” where appropriate.

<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Instruction/Assessment Item Modifications</u></b></p>
In addition to the overall Surgency, Negative Affect and Effortful Control scales that are derived from the validated IBQ-R-VSF, the HBCD Workgroup and measure experts added a Behavior Inhibition (or Social Fear) scale using items from the long form of the IBQ-R (IBQ-R-LF): 

<details>
<summary>Items added to IBQ-R-VSF from IBQ-R-LF</summary>
<ul>
<li>38. When introduced to an unfamiliar adult, how often did the baby hang back from the adult?</li>
<li>39. When introduced to an unfamiliar adult, how often did the baby never “warm up” to the unfamiliar adult?</li>
<li>40. When in the presence of several unfamiliar adults, how often did the baby cry?</li>
<li>41. When in the presence of several unfamiliar adults, how often did the baby continue to be upset for 10 minutes or longer?</li>
<li>42. When visiting a new place, how often did the baby show distress for the first few minutes?</li>
<li>43. When visiting a new place, how often did the baby continue to be upset for 10 minutes or more?</li>
<li>44. When your baby was approached by an unfamiliar person when you and your baby were out (for example, shopping), how often did the baby show distress?</li>
<li>45. When your baby was approached by an unfamiliar person when you and your baby were out (for example, shopping), how often did the baby cry?</li>
<li>46R. When an unfamiliar person came to your home or apartment, how often did your baby allow themselves to be picked up without protest?</li>
<li>47. When an unfamiliar person came to your home or apartment, how often did your baby cry when the visitor attempted to pick them up?</li>
</ul>
</details><br>


## Quality Control & Known Issues    
QC procedures included examining the range of the child’s age to ensure that it falls within 3 to 18 months; examining missingness; generating summary statistics and visualizations for item-level frequencies, age, and scores; and using Calculate Cronbach's Alpha for reliability. A common error noted during QC was that scoring was not accurately applied to observations with missing responses and incorrect administration ages. No potential issues were flagged by subject matter experts.

## Additional Information
 * [Mary Rothbart's Temperament Questionnaires](https://research.bowdoin.edu/rothbart-temperament-questionnaires)

## References 
- Gartstein, M. A., & Rothbart, M. K. (2003). Studying infant temperament via the Revised Infant Behavior Questionnaire. *Infant Behavior & Development*, 26(1), 64–86. [https://doi.org/10.1016/s0163-6383(02)00169-8](https://doi.org/10.1016/s0163-6383(02)00169-8)
- Putnam, S. P., Helbig, A. L., Gartstein, M. A., Rothbart, M. K., & Leerkes, E. (2014). Development and assessment of short and very short forms of the infant behavior questionnaire-revised. *Journal of Personality Assessment*, 96(4), 445–458. [https://doi.org/10.1080/00223891.2013.841171](https://doi.org/10.1080/00223891.2013.841171)
- Rothbart, M. K. (1981). Measurement of temperament in infancy. *Child Development*, 52(2), 569–578. [https://doi.org/10.1111/j.1467-8624.1981.tb03082.x](https://doi.org/10.1111/j.1467-8624.1981.tb03082.x)