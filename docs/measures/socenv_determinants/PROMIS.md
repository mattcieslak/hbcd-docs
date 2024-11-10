# Perceived Stress/Social Support
## Measure Overview
**Full Name**: Patient-Reported Outcome Measurement Information System  
**Acronym/Brief Name**: PROMIS    
**Construct**: Perceived Stress/Social Support      

**Description**     
These measures of perceived stress and social support are a combination of the PROMIS emotional support 4a questionnaire and the Perceived Stress Scale – 4 (PSS-4). The first 4 questions are the PROMIS emotional support 4a questionnaire which measures the quality of the emotional support to which the participant has access. The last 4 questions (PSS-4) represent the shortened version of the PSS-14. This questionnaire measures perceived general stress in the past month. It has been used in many populations world wide including pregnant individuals and young families.   

**Summary**     
The Perceived Stress and Social support tools measure perceived stress and perceptions of emotional support by one’s social network in the caregivers in this study longitudinally.       

## Implementation & Data Collection
**Method of Administration**: Remote survey       
**REDCap Form Name**: `sed_bm_strsup`     
**Pilot Data Dictionary**: PROMIS        
**Spanish Translation**: Existing        
**Child Specific/Unspecific Form**: Child Specific  
**Respondent:** Caregiver   
**Visits**: V01 (prenatal), V02 (0-1 month), V03 (3-9 months)   
**Estimated length of time for completion**: 4 minutes 

## HBCD Modifications
<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Answer/Response Option Changes</u></b></p>
Addition of “Don’t know” and “Decline to answer”

<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Scoring Changes</u></b></p>
Orignally, all items had to be completed to allow for scoring via the tables provided in the manual. For HBCD, this was updated so that items with “don’t know” answers will not have a total score reported.

For the PROMIS emotional support, complete data is necessary to use scoring tables provided in the manual. If scoring will utilize the PROMIS HealthMeasures Scoring Service, total scores can include missing data (this can be done by individual investigators). Complete data is always necessary to calculate a score PSS-4, therefore should not be reported for participants who answer any questions “don’t know.”

## Quality Control & Known Issues   
QC procedures involved monitoring the data dashboard for variable missingness, possible coding errors, scoring verification when needed, and data consistency. No potential issues were identified via the QC procedures or flagged by subject matter experts.

## Additional Information
Relevant Documents: Scoring Manuals


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
<li>Cohen, S., Kamarck, T., &amp; Mermelstein, R. (1983). A global measure of perceived stress. <em>Journal of Health and Social Behavior</em>, 24(4), 385–396. <a href="https://doi.org/10.2307/2136404">https://doi.org/10.2307/2136404</a></li>

<li>Hahn, E. A., Cella, D., Bode, R. K., &amp; Hanrahan, R. T. (2010). Measuring social well-being in people with chronic illness. <em>Social Indicators Research</em>, 96(3), 381–401. <a href="https://doi.org/10.1007/s11205-009-9484-z">https://doi.org/10.1007/s11205-009-9484-z</a></li>
</ul>
</details>
</body>
</html>
<br>