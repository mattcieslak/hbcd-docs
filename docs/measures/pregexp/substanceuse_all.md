# Substance Use Measures
## Constructs & Implementation
Substance use measures include ASSIST V1, ASSIST V2, and ASSIST V3 measures (**Full Name**: NIDA-modified Alcohol, Smoking and Substance Involvement Screening Test (ASSIST) V1.0/V2.0/V3.0) and TLFB (**Full Name**: Timeline Follow Back). Here is a summary of each construct and their implementation:

| REDCap Name  | Construct | Respondant | Time | Visit |
| - | - | - | - | - |
| `Assist V1`| Substance use before and during pregnancy | pregnant person | 5 min | V1 |
| `Assist V2` | Substance use (end of pregnancy and postnatal) | person who gave birth | 5 min | V2 |
| `Assist V3` | Substance use after pregnancy | person who gave birth or primary caregiver | 3 min | V3 |
| `TLFB` | Substance use before and during pregnancy | person who gave birth or primary caregiver | 10 min | V1, V2 |

In addition, the following implementations were common to all measures:  
**Method of Administration**: RA administered in person (except in Alabama, where it was self-administered)     
**Spanish Translation**: Created  
**Child Specific/Unspecific Form**: Unspecific  

## Detailed Descriptions
### ASSIST V1
**Description**: This was a created to capture maternal substance use before, during and after pregnancy  
**Summary**: Lifetime and problematic use, pre-pregnancy and pregnancy use was expanded into the following substances: nicotine or tobacco products, alcohol, cannabis, cannabidiol, synthetic cannabinoids, prescription opioids, heroin or other illicit opioids, methadone, buprenorphine, benzodiazepines, cocaine, amphetamine type stimulants, methamphetamine, inhalants, hallucinogens or club drugs, androgenic anabolic steroids, phencyclidine, and kratom. Participants were asked for each substance whether they had ever used it, and for those endorsed, a series of questions about disordered use or use causing problems in their lives. Information was obtained about modes of use specific to each substance. For example, for tobacco, participants were asked to report the type of product used, such as cigarettes or e-cigarettes. Likewise, participants who used cannabis were asked what types of products they used, such as smoking marijuana flower, vaping, or consuming edibles. If alcohol was reported during this period, the participant was further asked what type of alcohol they consumed (beer, hard cider, hard seltzer/wine/spirits). For each one, they were asked, on average, the volume of one typical glass/container that they consumed. United States defined ‘standard drinks’ were then calculated by dividing the amount reported by 12oz (beer, hard cider, hard seltzer), 5oz (wine) or 1.5 oz (spirits). Finally, if the participant reported opioids, they were asked the type of opioid used during the period, and typical quantities per occasion for the following: heroin (grams, bags), prescription opioids (pills), buprenorphine (pills, injectables, films), and methadone (mg). Any endorsement of substances in the 3 months prior to pregnancy or during pregnancy triggered the Time Line Follow Back (TLFB).

### ASSIST V2
**Description**: This was a created to capture maternal substance use between enrollment and delivery and postnatal (weeks 0-4) substance use.      
**Summary**: Participants were first asked to update whether they had used any of the 18 substances of interest between V1 and delivery. If alcohol was reported during this period, the participant was further asked what type of alcohol they consumed (beer, hard cider, hard seltzer/wine/spirits). For each one, they were asked, on average, the volume of one typical glass/container that they consumed. United States defined ‘standard drinks’ were then calculated by dividing the amount reported by 12oz (beer, hard cider, hard seltzer), 5oz (wine) or 1.5 oz (spirits). Finally, if the participant reported opioids, they were asked the type of opioid used during the period, and typical quantities per occasion for the following: heroin (grams, bags), prescription opioids (pills), buprenorphine (pills, injectables, films), and methadone (mg). Any endorsement of substances between V1 and delivery triggered the Time Line Follow Back (TLFB).   
In addition, participants were asked if they used any of the 18 substances between delivery and V2 (0-4 weeks postnatal). Response choices are: 0, Never | 1, Once or Twice | 2, Monthly | 3, Weekly | 4, Daily or Almost Daily.

### ASSIST V3
**Description**: This was a created to capture maternal substance use throughout the rest of the study.  
**Summary**: Participants were asked if they used any of the 18 substances in the last 3 months. Response choices are: 0 (Never), 1 (Once or Twice), 2 (Monthly), 3 (Weekly), 4 (Daily or Almost Daily).

### Timeline Follow Back 
**Description**: This was a created to capture maternal substance use before and during pregnancy  
**Summary**: Participants who reported any substance use in the three months before or during pregnancy were interviewed about their use of each substance with a TLFB approach.  They were instructed to report their substance use during 9 weeks in total for each substance reported on the ASSIST, disaggregated into product type (e.g. edible cannabis products). The number of occasions of use per day was captured for all products except for cigarettes and cigarillos (number per day) and alcohol (number of single servings per day). The sampled weeks captured 9 weeks in total and were as follows: pre-pregnancy use (Weeks 1-2: four weeks before LMP through two weeks before LMP), early pregnancy use (Weeks 3-6: two weeks after LMP through six weeks after LMP), and current use (Week 7: the week prior to V1). The TLFB was repeated at V2 to capture substance use during the last two full weeks of gestation (Weeks 8-9). While for most participants, the TLFB was administered by study staff, at the site where prenatal substance use was reportable by study staff, participants received training to enter their use directly into the TLFB.  

## Quality Control & Known Issues
### ASSIST V1 & V2
**QC Procedures**: Distributions for answers, cross with TLFB   
**Common Issues Identified**: If a participant endorsed a substance on the TLFB, it should have been noted on the Assist. Sometimes it was not, which triggered a query to the site to correct it.      
**Potential Issues Flagged by Subject Matter Experts**: To capture ‘standard drinks’ of alcohol, participants were asked to self-report their typical size of a single drink (in oz). This was difficult for some participants, and some reports are outside of expected range. Sites were queried on outliers, but participants were not always able to be re-contacted. 

### ASSIST V3
**QC Procedures**: Distributions for answers  
**Common Issues Identified**: None      
**Potential Issues Flagged by Subject Matter Experts**: None

### Timeline Follow Back
**QC Procedures**: Distributions for answers, cross with Assist     
**Common Issues Identified**: If a participant endorsed a substance on the TLFB, it should have been noted on the Assist. Sometimes it was not, which triggered a query to the site to correct it.      
**Potential Issues Flagged by Subject Matter Experts**  
Important note for users: the TLFB was a sampling of weeks of use before (Weeks 1-2) and during (Weeks 3-9) pregnancy. It is completely reasonable that someone could endorse a substance during pregnancy, and it doesn’t appear on the TLFB because it didn’t happen to fall within a sampled week. Similarly, they may have a positive biospecimen but no data on the TLFB for the same reason. Sampling (before, early, mid and late pregnancy) was meant to minimize participant burden (and not request a 40-week TLFB) but capture portions of pregnancy where behaviors tend to change (before and after pregnancy recognition, late pregnancy). 

Also of note- participants were asked to report occasions (except cigarettes/ cigarillos and drinks (number), but some substances (e.g. electronic cigarette devices) are difficult to report in occasions and have outliers.

The TLFB data should be combined with the biospecimen and Assist data. One could also create trajectories of use from the TLFB with assumptions by using data on early pregnancy (weeks 3-6) carried forward until stated pregnancy recognition (V1 Health), then using enrollment (week 7) information and carrying that forward until late pregnancy (weeks 8-9). 

## References
- National Institute on Drug Abuse. (n.d.). *NIDA Modified ASSIST*.
- Sobell, L., & Sobell, M. (2000). Alcohol timeline follow-back (TLFB). In *Handbook of psychiatric measures.* (p. 477). American Psychiatric Association.