# Pregnancy Health Measures
<table border="1" cellspacing="0" cellpadding="5" style="width: 100%; max-width: 100%; table-layout: auto; word-wrap: break-word; font-size: 0.8em;">
<caption><p style="font-size: 1.8em; margin: 0 0 5px; text-align: left; font-style: normal;"><b>Implementation & Data Collection</b></p></caption>
    <colgroup>
        <col style="width: 15%;" />
        <col style="width: 20%;" />
        <col style="width: 30%;" />
        <col style="width: 15%;" />
        <col style="width: 10%;" />
        <col style="width: 10%;" />
    </colgroup>
    <tbody>
        <tr>
            <th style="white-space: normal;">Measure</th>
            <th style="white-space: normal;">Short/REDCap Name</th>
            <th style="white-space: normal;">Construct</th>
            <th style="white-space: normal;">Administration</th>
            <th style="white-space: normal;">Time (min)</th>
            <th style="white-space: normal;">Visit**</th>
        </tr>
        <tr>
            <td style="white-space: normal;">Pregnancy Health</td>
            <td style="white-space: normal;">Healthhx/<code>Healthhx</code></td>
            <td style="white-space: normal;">Pre-pregnancy and pregnancy health</td>
            <td style="white-space: normal;">self</td>
            <td style="white-space: normal;">5</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-Vaccines</td>
            <td style="white-space: normal;">Exp I vacc/<code>Vacc</code></td>
            <td style="white-space: normal;">Vaccines in pregnancy</td>
            <td style="white-space: normal;">self</td>
            <td style="white-space: normal;">3</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-Chronic Conditions</td>
            <td style="white-space: normal;">Exp I chroncond/<code>chroncond</code></td>
            <td style="white-space: normal;">Chronic conditions and sexually transmitted infections in pregnancy</td>
            <td style="white-space: normal;">self</td>
            <td style="white-space: normal;">3</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-Illness</td>
            <td style="white-space: normal;">Exp I illness/<code>illness</code></td>
            <td style="white-space: normal;">Illness in pregnancy</td>
            <td style="white-space: normal;">RA</td>
            <td style="white-space: normal;">3</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-ER/Hospitalizations</td>
            <td style="white-space: normal;">Exp I ERhosp/<code>ERhosp</code></td>
            <td style="white-space: normal;">ER visit or hospitalization in pregnancy</td>
            <td style="white-space: normal;">RA</td>
            <td style="white-space: normal;">5</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-Medications</td>
            <td style="white-space: normal;">Exp I Meds/<code>Meds</code></td>
            <td style="white-space: normal;">Prescription and over the counter medications in pregnancy</td>
            <td style="white-space: normal;">RA</td>
            <td style="white-space: normal;">5</td>
            <td style="white-space: normal;">V1</td>
        </tr>
        <tr>
            <td style="white-space: normal;">PH-V2 (End of Pregnancy)</td>
            <td style="white-space: normal;">Healthv2 Preg/<code>HealthV2 Preg</code></td>
            <td style="white-space: normal;">Updates information between enrollment and delivery</td>
            <td style="white-space: normal;">RA</td>
            <td style="white-space: normal;">10</td>
            <td style="white-space: normal;">V2</td>
        </tr>
    </tbody>
</table>
<sup>* V1 visits occurred during pregnancy and V2 occurred 0-1 months postnatal</sup> 

Implementation parameters consistent across all pregnancy health measures include **Spanish Translation** (*Created*), **Child Specific/Unspecific Form** (*Unspecific*), and **Respondent** (*Pregnant Person*).

### Details & Known Issues
**Pregnancy Health**      
This measures gravidity and parity, height and weight, pregnancy intentions, use of assisted reproductive technology, start of prenatal care, prenatal vitamin or aspirin use, secondhand smoke. No potential issues were noted by subject matter experts.

**PH- Vaccines**  
This measure Asks about receipt of a list of common vaccines in pregnancy, and trimester received.

**PH- Chronic Conditions**      
Asks about a pre-defined list of chronic conditions and sexually transmitted infections in pregnancy. Endorsed chronic conditions are asked whether they are ongoing or resolved.

**PH - Illness**    
Illnesses asks about covid-19 or other illnesses in pregnancy, including start and stop dates and whether the person had a fever. Illnesses are captured either from ICD codes (from BioPortal ICD) or symptom codes (from World Health Organization), which were at times difficult for the participant to name or the RA to correctly find in the ICD or symptom database.

**PH - ER/Hospitalizations**        
Reasons for ER visit or hospitalization during pregnancy are captured from ICD codes (from BioPortal ICD), which were at times difficult for the participant to name or the RA to correctly find in the ICD database. This was particularly apparent for use of the ER for normal care (no diagnosis) or false alarms (e.g. thought water broke but it did not), resulting in the use of ‘don’t know.’

**PH - Medications**     
This measure asks about any prescription or over the counter medications used since last menstrual period. For each, the participant is asked medication name, indication, frequency, start and stop date (if applicable). Medication was queried from the RxNORM database. Reasons for medication use are captured from ICD codes (from BioPortal ICD), which were at times difficult for the participant to name or the RA to correctly find in the ICD database. This was apparent with aspirin used for preeclampsia, as there was not an option for coding preventive use. Aspirin was specifically moved to the prenatal vitamin section a few months into the study. Additionally, medications used PRN were difficult for the participant to report. Finally, although not asked, some medications were coded with the dose in the database, although this was not asked and should not be used.

**PH - V2 (End of Pregnancy)**  
This measure updates information on prenatal vitamins, aspirin, infections, vaccines, prescription and over the counter medications (both continued from V1 and any new medications) and illnesses. In addition, we ask about pregnancy complications (from a list: e.g. gestational diabetes), labor, mode of delivery, place of delivery, and how many nights the birthing person remained in the hospital. Same issues identified at V1 (difficulty with ICD codes (from BioPortal ICD) and medication names (from RxNORM)) apply to this visit as well.   
