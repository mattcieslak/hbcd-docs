## Multilingual Language Development Screener
### Overview
**Full Name**: Multilingual Language Development Screener    
**Acronym/Brief Name**: MLDS    
**Construct**: Multilingual exposure       
**Description**: This measure is assessing the child’s exposure to languages and whether there are concerns about the child’s hearing. A series of forced choice questions were used to elicit the responses and slide scales were used to assess the percentage of time a child is exposed to a given language in their various environments (i.e., home, daycare, other family member household, babysitter). Up to ten non-parental childcare arrangements were sampled. The measure was designed to inform the site’s assessment team prior to assessments related to neurocognitive and language functioning. Responses are used to determine who was able to conduct the cognitive and language assessments (i.e., English or Spanish speaking) and to document additional challenges to completing assessments (hearing impairment, other languages). This was a questionnaire developed specifically for HBCD to inform assessment process. Caregivers opt for their child’s assessment to be performed in either English or Spanish for in person performance tasks (i.e., NIH Baby Toolbox, Bayley-4, or Deferred Imitation) by selecting between a forced choice of English or Spanish. For the MacArthur-Bates Communicative Development Inventories (CDI), an algorithm was used to determine if the CDI is done in English only, English and Spanish,  English only, or not at all.   
**Summary**: This instrument involves a series of questionnaires that assess parental concern regarding the child’s hearing and the presence of English, Spanish, or Other languages in the child’s home and childcare environments. 

### Implementation
**Method of Administration**: This measure is completed remotely by caregivers prior to when cognitive and language assessments will be performed. If the caregiver does not complete the assessment remotely, it is conducted at the visit to document the child’s language exposure environments. The instrument can be administered by an RA in person or via video as needed.    
**REDCap Form Name**: Child Language Exposure Survey    
**Pilot Data Dictionary**: ncl_ch_mlds  
**Spanish Translation**: Existing   
**Child Specific/Unspecific Form**: Child Specific  
**Respondent:** Primary caregiver of the child

### Data Collection
**Visits Administered and corresponding age range of administration**: Prior to all visits where cognitive and language assessments were done (V3, V4, V5, V6, V7, V8) 
**Estimated length of time for completion**: 3-10 minutes

### Quality Control (QC)
**QC Procedures**   
Frequency of decline to answer and completeness was monitored during data collection.

**Common Issues Identified**    
From initial data about 10% of questionnaires are not complete.

### Potential Issues Flagged by Subject Matter Experts
None

### Scoring Algorithms
#### For up to 10 non-parental childcare arrangements: 

**Total days each week** = On average, how days each week is your child cared for in non-parental childcare arrangement?:  (Daycare + With Babysitter + With other family members outside of the household + Other non-parental childcare arrangement)

**Total hours per day**= On average, how many hours per day is your child cared for in non-parental childcare arrangement?:  (Daycare + With Babysitter + With other family members outside of the household + Other non-parental childcare arrangement)

**To determine total out of home hours for each of the environments**, days per week * total hours per day was computed. This was then multiplied by the percentage of English and Spanish  language endorsed per environment. A frequency of English and Spanish is provided for each care environment.

**Total hours per week spent at non-parental arrangements** is added across the potential 10 environments

The total frequency of Spanish and English was computed by multiplying the percentage of English and Spanish by the total hours per week in both the home and other care environments. The values are provided for home and for the overall total child experience, combining home and other care environments.

#### The algorithm used to assess English or Spanish CDI administration is as follows:
 * only in Spanish: child’s language environment has >= 30% Spanish AND < 30% English
 * only in English: child’s language environment has >= 30% English AND < 30% Spanish
 * in both languages (still pending Steering Committee voting): child’s language environment has >= 30% Spanish AND >= 30% English
 * neither Spanish nor English: child’s language environment has < 30% Spanish AND < 30% English
