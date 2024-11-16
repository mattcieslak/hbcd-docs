# Nails
**Full Name**: Nails       
**Construct**: Toxicology screen, fingernails and toenails     
**Description**: Results of toxicology assays in nails collected at V1 and V2


<details>
<summary>Implementation & Data Collection Details</summary>
<ul>
<br>
<p><strong>Method of Administration</strong>: Self-collected under research team supervision, or collected by research team <br />
<strong>Respondent:</strong> Pregnant/Postpartum person <br />
<strong>Visits</strong>: V01, V02 <br />
<strong>Estimated length of time for completion</strong>: 5 minutes</p>
</details>

## Quality Control & Known Issues
QC procedures involved examining assay ranges and categorical versus continuous measures. No common issues were identified from QC.

One potential issue flagged by subject matter experts is that the nail processing workflow was re-developed and implemented on July 1, 2024. The revised workflow considers the amounts of specimen available and offers the opportunity for additional confirmation tests in case of low sample quantity. It uses the remnants of the ELISA extract for confirmation saving an additional 20 mg of nail sample. Specimens are sorted by weight. An additional 20 mg of specimen is required for each LCMSMS confirmation, and if additional specimen is not available, the remnant of ELISA extract is used for confirmation (Figure 1). 

#### Figure 1. Schematic for nail processing
<img src="Fig1_nails.png" width="75%" height="auto">

- Specimens that contain at least 20 mg of nail are screened using ELISA with subsequent LCMSMS confirmation for presumptive positives. An additional 20 mg of specimen is required for each LCMSMS confirmation, and if additional specimen is not available, the remnant of ELISA extract is used for confirmation.
- Specimens containing between 10 and 20 mg of nail go directly to LCMSMS for EtG, which is the only test conducted. 
- Specimens containing 30 mg or more sample, both 14-panel test and EtG are conducted.
- Nail weights and test ordered (custom 14 panel test; EtG only; cancelled) are noted in data dictionary (Table 1).

<details>
  <summary>Table 1. Sample data dictionary nail assays</summary>
  <br>
  <table class="docutils">
    <thead>
      <tr>
		<th>Variable</th>
		<th>Description</th>
		<th>Form</th>
		<th>Options</th>
	   </tr>
	</thead>
	<tbody>
	<tr>
		<td>Specimen_ID</td>
		<td>Specimen ID</td>
		<td>String</td>
		<td>String</td>
	</tr>
	<tr>
		<td>PSCID</td>
		<td>Participant ID</td>
		<td>String</td>
		<td>String</td>
	</tr>
	<tr>
		<td>Visit_time_point</td>
		<td>Visit time point</td>
		<td>Categorical</td>
		<td>1: visit 1<br />2: visit 2</td>
	</tr>
	<tr>
		<td>Nail_weight</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Weight of nails available to assay</td>
		<td>Continuous</td>
		<td>nail weight (grams)</td>
	</tr>
	<tr>
		<td>Nail_type</td>
		<td>Type of nails assayed</td>
		<td>Categorical</td>
		<td>1: fingernail<br />2: toenail<br />3: both<br />4: unknown</td>
	</tr>
	<tr>
		<td>test_ordered_n</td>
		<td>Test ordered</td>
		<td>Categorical</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">1: custom 14 panel test<br />2: Only enough to run EtG<br />3: Canceled because we could not run anything (no results generated)</td>
	</tr>
	<tr>
		<td>c_any_specimen_n</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Specimen level result (positive for any analyte in confirmatory tests)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: QNS</td>
	</tr>
	<tr>
		<td>c_any_stim_n</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Any stimulants in nails (based on confirmatory results for amphetamine, methamptheamine, MDM, MDA, MDEA)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: QNS</td>
	</tr>
	<tr>
		<td>s_amp_n</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Screening test in nails: amphetamine/MDA dual test (amp/mamp)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: QNS</td>
	</tr>
	<tr>
		<td>s_mamp_n</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Screening test in nails: methamphetamine/MDMA dual test (amp/mamp)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: QNS</td>
	</tr>
	<tr>
		<td>c_amp_n_cat</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Confirmatory test in nails: amphetamine (categorical) (amp/mamp)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: QNS<br />4: screen negative</td>
	</tr>
	<tr>
		<td>c_amp_n</td>
		<td style="width: 180px; word-wrap: break-word; white-space: normal;">Confirmatory test in nails: amphetamine (amp/mamp)</td>
		<td>Continuous</td>
		<td>concentration value; -999</td>
	</tr>
</tbody>
</table>
</details>


## Additional Information

Substances that were tested by USDTL, excluding those cancelled due to insufficient quality or quantity, followed these rules:

- If any substance analyte (e.g. Amphetamine (c_amp_n)) confirmatory test is positive based on predefined thresholds (Table 2), the class-level (c_any_stim_n) and sample-level (c_any_specimen_n) are also positive (value =1). 
- Otherwise, if all substance analyte confirmatory tests are negative (e.g., c_nic_n and c_ cot_n, values = 0) then class-level (e.g., c_nictotine_u) are negative (value =0). If all classes are negative (value = 0), then sample-level (e.g., c_any_specimen_n) are negative (value = 0). 
- Finally, if there was not enough sample for any substance analyte confirmatory tests the test is coded quantity not sufficient (QNS; value = 3) and the class-level, and sample-level values are also QNS (value = 3)
- Continuous variables should be interpreted with caution based on the limits of quantification (LOQs) in Table 2. 
- All class-level groupings by analyte screening tests and analyte confirmatory tests are shown in Table 3.


<details>
  <summary>Table 2. Nail Assay Thresholds </summary>
  <table class="docutils">
  <br>
    <thead>
      <tr>
        <th>Analyte</th>
        <th>LOD<br />(pg/mL)</th>
        <th>LOQ<br />(pg/mL)</th>
        <th>Cutoff<br />(pg/mL)</th>
        <th>Detection Window</th>
      </tr>
    </thead>
    <tbody>
	<tr>
		<td>Amphetamine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Methamphetamine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>MDA</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>MDMA</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>MDEA</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Carboxy-delta-9-THC</td>
		<td>0.01</td>
		<td>0.02</td>
		<td>0.05</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Cocaine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Cocaethylene</td>
		<td>10</td>
		<td>20</td>
		<td>50</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Benzoylecgonine</td>
		<td>10</td>
		<td>20</td>
		<td>50</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norcocaine</td>
		<td>10</td>
		<td>20</td>
		<td>50</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>6-MAM</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Codeine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Hydrocodone</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Hydromorphone</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Morphine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norhydrocodone</td>
		<td>8</td>
		<td>16</td>
		<td>40</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Oxycodone</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Oxymorphone</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Noroxycodone</td>
		<td>8</td>
		<td>16</td>
		<td>40</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Methadone</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>EDDP</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Amobarbital</td>
		<td>80</td>
		<td>80</td>
		<td>200</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Butalbital</td>
		<td>80</td>
		<td>80</td>
		<td>200</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Pentobarbital</td>
		<td>80</td>
		<td>80</td>
		<td>200</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Phenobarbital</td>
		<td>80</td>
		<td>80</td>
		<td>200</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Secobarbital</td>
		<td>80</td>
		<td>80</td>
		<td>200</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Alprazolam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Diazepam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Midazolam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Nordiazepam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Oxazepam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Temazepam</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Ketamine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norketamine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Tramadol</td>
		<td>200</td>
		<td>400</td>
		<td>500</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Fentanyl</td>
		<td>2</td>
		<td>4</td>
		<td>10</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norfentanyl</td>
		<td>2</td>
		<td>4</td>
		<td>10</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Alfentanil</td>
		<td>2</td>
		<td>4</td>
		<td>10</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Acetyl Fentanyl</td>
		<td>2</td>
		<td>4</td>
		<td>10</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Acetyl Norfentanyl</td>
		<td>2</td>
		<td>4</td>
		<td>10</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Sufentanil</td>
		<td>1</td>
		<td>2</td>
		<td>5</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norsufentanil</td>
		<td>2</td>
		<td>2</td>
		<td>5</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Buprenorphine</td>
		<td>4</td>
		<td>8</td>
		<td>20</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Norbuprenorphine</td>
		<td>4</td>
		<td>8</td>
		<td>20</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Ethyl glucuronide</td>
		<td>4</td>
		<td>8</td>
		<td>20</td>
		<td>Finger 3 months <br /> Toe no consensus*</td>
	</tr>
	<tr>
		<td>Nicotine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
	</tr>
	<tr>
		<td>Cotinine</td>
		<td>20</td>
		<td>40</td>
		<td>100</td>
		<td>Finger 3-6 months Toe 10-14 months</td>
</tr>
</tbody>
</table>
<i>LOD: limit of detection; LOQ: limit of quantification: Cutoff concentration used to categorize metabolite as positive/negative</i>
</details>


<details class="collapsible references">
  <summary class="references">References</summary>
 <ul>
    <li>Bandoli, G., Anunziata, F., Bogdan, R., Zilverstand, A., Chaiyachati, B. H., Gurka, K. K., Sullivan, E., Croff, J., & Bakhireva, L. N. (2024). Assessment of substance exposures in nail clipping samples: A systematic review. <i>Drug and Alcohol Dependence</i>, 254, 111038. <a href="https://doi.org/10.1016/j.drugalcdep.2023.111038" target="_blank">https://doi.org/10.1016/j.drugalcdep.2023.111038</a></li>
  </ul>
</details>


 
