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
**Visits**: Visit 3 (<12 months in age), Visit 4, Visit 6  
**Estimated length of time for completion**: 1-2 minutes

## HBCD Modifications
<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Global Measure Changes</u></b></p>
Alterations were made to items for use of gender-neutral terms. Individual items containing gendered pronouns (‘his/hers’, ‘he/she’) were edited to either eliminate the pronouns entirely or replace gendered pronouns with ‘my baby’ when eliminating pronouns was not grammatically possible. 

The original ecPROMIS – Child Caregiver Interaction items reference ‘my child’ rather than ‘my baby’, as the original measure is intended for 1-5-year-old children. To be developmentally appropriate for the pre-V03 age window (3 months – 9 months), however, items were adapted per the guidance of ecPROMIS developers Dr. Dave Cella and Dr. Courtney Blackwell to reference ‘my baby.’

Per the HBCD DEI Committee’s recommendations: (1) the variable `peer_yn` was added (unique to HBCD) and (2) for Self-Regulation- Flexibility, the item queue order for original items 1-5 was rearranged to the order: 2, 3, 4, 5, 1.

Because ecPROMIS measures are copyrighted, it is important that future publications account for edits made to individual items as part of both HBCD DEI review and for developmental appropriateness. Especially if investigators filter by the `peer_yn` variable, it should be acknowledged that this item was not part of the original measure.

<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Instruction/Assessment Item Modifications</u></b></p>
<table dir="ltr" border="1" cellspacing="0" cellpadding="0" data-sheets-root="1" data-sheets-baot="1"><colgroup><col width="100" /><col width="100" /><col width="100" /><col width="100" /><col width="100" /><col width="100" /></colgroup>
<tbody>
<tr>
<td>Item</td>
<td>Original Item Text</td>
<td colspan="4" rowspan="1">HBCD Item Text</td>
</tr>
<tr>
<td>peer_yn**</td>
<td>NA - item added specifically for HBCD</td>
<td colspan="4" rowspan="1">My child had opportunities to interact with other children.</td>
</tr>
<tr>
<td>ecpromis1</td>
<td>My child was good at expressing his/her needs to me or other parent.</td>
<td colspan="4" rowspan="1">My baby was good at expressing needs to me or other parent.</td>
</tr>
<tr>
<td>ecpromis2</td>
<td>My child was affectionate with me or other parent.</td>
<td colspan="4" rowspan="1">My baby was affectionate with me or other parent.</td>
</tr>
<tr>
<td>ecpromis3</td>
<td>My child sought comfort from me or other parent.</td>
<td colspan="4" rowspan="1">My baby sought comfort from me or other parent.</td>
</tr>
<tr>
<td>ecpromis4</td>
<td>My child came to me or other parent for help when he/she needed it.</td>
<td colspan="4" rowspan="1">My baby let me know when my baby needed help.</td>
</tr>
<tr>
<td>ecpromis5</td>
<td>My child was excited to spend time with me or other parent.</td>
<td colspan="4" rowspan="1">My baby was excited to see me or other parent after being apart.</td>
</tr>
</tbody>
</table>
<i>**Added to the beginning of the survey instrument per the HBCD DEI Committee’s recommendation. `peer_yn` is not scored: possible responses include 0 (No), 1, (Yes), and Decline to Answer</i>

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


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>REFERENCES</title>
  <style>
    .collapsible {
      background-color: #7cceb3;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
    }
    details {
      background-color: #f1f1f1;
      padding: 10px;
      margin: 10px 1;
      border-radius: 5px;
    }
    summary {
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }
    a {
      color: #007BFF;
      text-decoration: none;
    }
  </style>
</head>
<body>
<details class="collapsible">  
  <summary><b>REFERENCES <i>(click to expand)</i></b></summary> 
  <br> 
  <ul>  
    <li>Blackwell, C. K., Lai, J.-S., Kallen, M., Bevans, K. B., Davis, M. M., Wakschlag, L. S., & Cella, D. (2022). Measuring PROMIS® Social Relationships in early childhood. <i>Journal of Pediatric Psychology</i>, 47(5), 573–584. <a href="https://doi.org/10.1093/jpepsy/jsac031" target="_blank">https://doi.org/10.1093/jpepsy/jsac031</a></li>  
    <li>Cella, D., Blackwell, C. K., & Wakschlag, L. S. (2022). Bringing PROMIS to Early Childhood: Introduction and qualitative methods for the development of Early Childhood Parent Report instruments. <i>Journal of Pediatric Psychology</i>, 47(5), 500–509. <a href="https://doi.org/10.1093/jpepsy/jsac027" target="_blank">https://doi.org/10.1093/jpepsy/jsac027</a></li>  
    <li>Lai, J.-S., Kallen, M. A., Blackwell, C. K., Wakschlag, L. S., & Cella, D. (2022). Psychometric considerations in developing PROMIS® measures for early childhood. <i>Journal of Pediatric Psychology</i>, 47(5), 510–522. <a href="https://doi.org/10.1093/jpepsy/jsac025" target="_blank">https://doi.org/10.1093/jpepsy/jsac025</a></li>  
    <li>Park, C. H., Blaisdell, C. J., & Gillman, M. W. (2022). The NIH ECHO program: An impetus for the development of early childhood PROMIS tools. <i>Journal of Pediatric Psychology</i>, 47(5), 497–499. <a href="https://doi.org/10.1093/jpepsy/jsac010" target="_blank">https://doi.org/10.1093/jpepsy/jsac010</a></li>  
  </ul>  
</details>  

</body>
</html>
<br>
