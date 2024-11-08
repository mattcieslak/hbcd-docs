# Substance Use Measures
## Constructs & Implementation
Substance use measures include Assist V1, Assist V2, and Assist V3 measures (**Full Name**: NIDA-modified Alcohol, Smoking and Substance Involvement Screening Test (ASSIST) V1.0/V2.0/V3.0) and TLFB (**Full Name**: Timeline Follow Back). Here is a summary of each construct and their implementation:

| REDCap Name  | Construct | Respondant | Time | Visit |
| - | - | - | - | - |
| `Assist V1`| <sup>Substance use before and during pregnancy</sup> | <sup>Pregnant person</sup> | 5 min | V1 |
| `Assist V2` | <sup>Substance use (end of pregnancy and postnatal)</sup> | <sup>Person who gave birth</sup> | 5 min | V2 |
| `Assist V3` | <sup>Substance use after pregnancy</sup> | <sup>Person who gave birth<br>or primary caregiver</sup> | 3 min | V3 |
| `TLFB` | <sup>Substance use before and during pregnancy</sup> | <sup>Person who gave birth<br>or primary caregiver</sup> | 10 min | V1, V2 |

In addition, the following implementations were common to all measures:  
**Method of Administration**: RA administered in person (except in Alabama, where it was self-administered)     
**Spanish Translation**: Created  
**Child Specific/Unspecific Form**: Unspecific  

## HBCD Modifications
<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Assist: Global Measure Changes</u></b></p>

The **Assist measures** were created from combining the Family History Assessment Module (FHAM) and the All of Us Personal and Family Health History, which was then modified from the [NIDA Quick Screen (Modified Assist)](https://nida.nih.gov/sites/default/files/pdf/nmassist.pdf). The original quick screen was scored; however, our version is not scored. To acknowledged these changes in future publications: authors can note that questions were motivated from the NIDA Modified Assist.

<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>Assist: Instruction/Assessment Item Modifications</u></b></p>  
The NIDA quick screen tool (have you used alcohol, tobacco, prescription drugs, or illegal drugs in the last year) was removed and replaced by questions to assess more details regarding substances used and the timeline of their use before and during pregnancy. Please expand each section below to see specifics on added options/questions:

<div style="margin-bottom: 5px;">
<details>
<summary>Added additional substance options for questions listing substance options</summary>
<ul>
  <li>Nicotine or tobacco products (cigarettes, e-cigarettes, chewing tobacco, cigars, etc.)</li>
  <li>Alcoholic beverages (beer, wine, spirits, etc.)</li>
  <li>Cannabis (marijuana, weed, pot, hash, wax, blunts, dabs, gummies, vapes, etc.)</li>
  <li>Cannabidiol (CBD; not containing THC)</li>
  <li>Synthetic cannabinoids (K2, spice, etc.)</li>
  <li>Prescription opioids (oxycodone, morphine, codeine, fentanyl, tramadol, etc.)</li>
  <li>Heroin or other illicit opioids (fentanyl, oxycodone, etc.)</li>
  <li>Methadone</li>
  <li>Buprenorphine</li>
  <li>Benzodiazepines, sedatives, or sleeping pills (Valium, Xanax, Ambien, barbiturates, etc.)</li>
  <li>Cocaine (coke, crack, etc.)</li>
  <li>Amphetamine type stimulants (speed, Adderall, diet pills, etc.)</li>
  <li>Methamphetamine (meth, crystal meth, etc.)</li>
  <li>Inhalants (nitrous, glue, petrol, paint thinner, etc.)</li>
  <li>Hallucinogens or club drugs (LSD, acid, mushrooms, psilocybin, MDMA, molly, ecstasy, Special K, GHB, etc.)</li>
  <li>Androgenic anabolic steroids (for performance enhancement)</li>
  <li>Phencyclidine (PCP)</li>
  <li>Kratom</li>
</ul>
</details>
</div>


<div style="margin-bottom: 5px;">
<details>
<summary>Replaced questions 2-8 with questions specific to Assist V1, V2, and V3</summary>
<ul>
<br>
<u>For Assist V1, questions 2-8 were replaced with the following to assess lifetime use:</u>
	<li>Have you EVER been concerned about your use of this substance or worried it was problematic use?</li>
	<li>Has a friend, relative, or anyone else EVER expressed concern about your use of this substance</li>
	<li>Have you EVER tried and failed to control, cut down, or stop using this substance?</li>
	<li>Have you EVER sought or received treatment related to your use of this substance by a medical provider, spiritual leader, community mutual help group (like AA or SMART Recovery), counselors, or in other settings</li>
	<li>Have you EVER been clinically diagnosed with abuse, dependence, or a substance use disorder related to your use of this substance</li>
	<li>Have you EVER taken (prescribed or otherwise) medication(s) as treatment for a problem substance</li>
<u>For Assist V2, questions 2-8 were replaced with the following to assess use after pregnancy:</u>
	<li>FROM THE TIME THAT YOU DELIVERED your child until now, how often have you used any of the following substances for any reason [followed by list of substance options from section above]</li>
<u>For Assist V3, questions 2-8 were replaced with the following to assess impact of substance use after pregnancy:</u>
	<li>DURING THE PAST THREE MONTHS, has your use of this substance led to physical or mental health, social,or financial problems?</li>
    <li>DURING THE PAST THREE MONTHS, have you ever failed to do what was normally expected of you  (like work, go to school, be a parent, or household tasks) because of your use of this substance?</li>
</ul>
</details>
</div>

<div style="margin-bottom: 5px;">
<details>
<summary>Assist V1 only: Added 3 additional questions to screen for any substance use in the 3 months prior to pregnancy or during pregnancy, which then triggers a timeline follow back</summary>
<ul>
	<li>IN THE THREE MONTHS BEFORE YOU BECAME PREGNANT, which of the following substances have you ever used for any reason (and same options as in #1)</li>
	<li>DURING YOUR PREGNANCY, which of the following substances have you ever used for any reason? (and same options as in #1)</li>
	<li>When you were using alcohol during the THREE MONTHS BEFORE or DURING YOUR PREGNANCY, please select the specific substances you used below: breaks apart type of alcohol, cannabinoid, stimulant, tobacco, hallucinogen, and opioid.</li>
</ul>
</details>
</div><br>

<p style="font-size: 1.2em; margin: 0 0 5px;"><b><u>TFLB Modifications for HBCD</u></b></p>
The [original TLFB](https://cde.nida.nih.gov/sites/nida_cde/files/TimeLineFollowBack_2014Mar24.pdf) was modified to meet the needs of the HBCD study. The original TLFB covers the last 7 days. For the HBCD study, the following timeframes are queried:

- Visit 1: LMP – 4 through LMP – 2, LMP + 2 through LMP + 6, Last week prior to V1 (enrollment)
- Visist 2: Last 2 full calendar weeks prior to delivery (to mask the child’s DOB)

In addition, regarding answer/response option changes: for all substances except Alcohol, instead of getting Y/N per day, we ask number of times used/day (frequency of use).

## Detailed Descriptions
### ASSIST V1
**Description**     
This was a created to capture maternal substance use before, during and after pregnancy  

**Summary**     
Lifetime and problematic use, pre-pregnancy and pregnancy use was expanded into the following substances: nicotine or tobacco products, alcohol, cannabis, cannabidiol, synthetic cannabinoids, prescription opioids, heroin or other illicit opioids, methadone, buprenorphine, benzodiazepines, cocaine, amphetamine type stimulants, methamphetamine, inhalants, hallucinogens or club drugs, androgenic anabolic steroids, phencyclidine, and kratom. Participants were asked for each substance whether they had ever used it, and for those endorsed, a series of questions about disordered use or use causing problems in their lives. Information was obtained about modes of use specific to each substance. For example, for tobacco, participants were asked to report the type of product used, such as cigarettes or e-cigarettes. Likewise, participants who used cannabis were asked what types of products they used, such as smoking marijuana flower, vaping, or consuming edibles. If alcohol was reported during this period, the participant was further asked what type of alcohol they consumed (beer, hard cider, hard seltzer/wine/spirits). For each one, they were asked, on average, the volume of one typical glass/container that they consumed. United States defined ‘standard drinks’ were then calculated by dividing the amount reported by 12oz (beer, hard cider, hard seltzer), 5oz (wine) or 1.5 oz (spirits). Finally, if the participant reported opioids, they were asked the type of opioid used during the period, and typical quantities per occasion for the following: heroin (grams, bags), prescription opioids (pills), buprenorphine (pills, injectables, films), and methadone (mg). Any endorsement of substances in the 3 months prior to pregnancy or during pregnancy triggered the Time Line Follow Back (TLFB).

### ASSIST V2
**Description**     
This was a created to capture maternal substance use between enrollment and delivery and postnatal (weeks 0-4) substance use.      

**Summary**     
Participants were first asked to update whether they had used any of the 18 substances of interest between V1 and delivery. If alcohol was reported during this period, the participant was further asked what type of alcohol they consumed (beer, hard cider, hard seltzer/wine/spirits). For each one, they were asked, on average, the volume of one typical glass/container that they consumed. United States defined ‘standard drinks’ were then calculated by dividing the amount reported by 12oz (beer, hard cider, hard seltzer), 5oz (wine) or 1.5 oz (spirits). Finally, if the participant reported opioids, they were asked the type of opioid used during the period, and typical quantities per occasion for the following: heroin (grams, bags), prescription opioids (pills), buprenorphine (pills, injectables, films), and methadone (mg). Any endorsement of substances between V1 and delivery triggered the Time Line Follow Back (TLFB).   
In addition, participants were asked if they used any of the 18 substances between delivery and V2 (0-4 weeks postnatal). Response choices are: 0 (Never), 1 (Once or Twice), 2 (Monthly), 3 (Weekly), 4 (Daily or Almost Daily).

### ASSIST V3
**Description**     
This was a created to capture maternal substance use throughout the rest of the study.  

**Summary**     
Participants were asked if they used any of the 18 substances in the last 3 months. Response choices are: 0 (Never), 1 (Once or Twice), 2 (Monthly), 3 (Weekly), 4 (Daily or Almost Daily).

### Timeline Follow Back 
**Description**     
This was a created to capture maternal substance use before and during pregnancy. The [original TLFB](https://cde.nida.nih.gov/sites/nida_cde/files/TimeLineFollowBack_2014Mar24.pdf) was modified for HBCD as described in the Visit Measure Changes of the Change Log.  

**Summary**         
Participants who reported any substance use in the three months before or during pregnancy were interviewed about their use of each substance with a TLFB approach.  They were instructed to report their substance use during 9 weeks in total for each substance reported on the ASSIST, disaggregated into product type (e.g. edible cannabis products). The number of occasions of use per day was captured for all products except for cigarettes and cigarillos (number per day) and alcohol (number of single servings per day). The sampled weeks captured 9 weeks in total and were as follows: pre-pregnancy use (Weeks 1-2: four weeks before LMP through two weeks before LMP), early pregnancy use (Weeks 3-6: two weeks after LMP through six weeks after LMP), and current use (Week 7: the week prior to V1). The TLFB was repeated at V2 to capture substance use during the last two full weeks of gestation (Weeks 8-9). While for most participants, the TLFB was administered by study staff, at the site where prenatal substance use was reportable by study staff, participants received training to enter their use directly into the TLFB.  

## Quality Control & Known Issues
### ASSIST V1 & V2
Response distributions were reviewed for outliers and crossed with TLFB. One common issue noted was that if a participant endorsed a substance on the TLFB, it should have been noted on the Assist. Sometimes it was not, which triggered a query to the site to correct it. One potential issue flagged by subject matter experts was that, to capture ‘standard drinks’ of alcohol, participants were asked to self-report their typical size of a single drink (in oz): this was difficult for some participants, and some reports are outside of expected range. Sites were queried on outliers, but participants were not always able to be re-contacted. 

### ASSIST V3
Response distributions were reviewed for outliers and no common issues were identified nor were any potential issues flagged by subject matter experts.

### Timeline Follow Back
Response distributions were reviewed for outliers and crossed with Assist. One common issue noted was that if a participant endorsed a substance on the TLFB, it should have been noted on the Assist. Sometimes it was not, which triggered a query to the site to correct it.   
   
**Potential Issues Flagged by Subject Matter Experts**  
Important note for users: the TLFB was a sampling of weeks of use before (Weeks 1-2) and during (Weeks 3-9) pregnancy. It is completely reasonable that someone could endorse a substance during pregnancy, and it doesn’t appear on the TLFB because it didn’t happen to fall within a sampled week. Similarly, they may have a positive biospecimen but no data on the TLFB for the same reason. Sampling (before, early, mid and late pregnancy) was meant to minimize participant burden (and not request a 40-week TLFB) but capture portions of pregnancy where behaviors tend to change (before and after pregnancy recognition, late pregnancy). 

Also of note- participants were asked to report occasions (except cigarettes/ cigarillos and drinks (number), but some substances (e.g. electronic cigarette devices) are difficult to report in occasions and have outliers.

The TLFB data should be combined with the biospecimen and Assist data. One could also create trajectories of use from the TLFB with assumptions by using data on early pregnancy (weeks 3-6) carried forward until stated pregnancy recognition (V1 Health), then using enrollment (week 7) information and carrying that forward until late pregnancy (weeks 8-9). 

## References
- National Institute on Drug Abuse. (n.d.). *NIDA Modified ASSIST*.
- Sobell, L., & Sobell, M. (2000). Alcohol timeline follow-back (TLFB). In *Handbook of psychiatric measures.* (p. 477). American Psychiatric Association.