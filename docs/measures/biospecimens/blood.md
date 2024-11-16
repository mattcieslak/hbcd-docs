# Blood
**Full Name**: Blood              
**Construct**: Toxicology screen, blood        
**Description**:  Results of toxicology assays in dried blood spots collected at V1

<details>
<summary>Implementation & Data Collection Details</summary>
<ul>
<br>
<p><strong>Method of Administration</strong>: Phlebotomist-collected venous blood, which is pipetted onto dried blood spot cards <br />
<strong>Respondent:</strong> Pregnant person <br />
<strong>Visits</strong>: V01 <br />
<strong>Estimated length of time for completion</strong>: 5 minutes</p>
</details>
<br>

Processing of Blood Spot Cards consists of preparing 3x 1/8” punches of dried blood spot followed by extraction using an organic solvent. Detection of PETH in the extract is accomplished with a single pass using LCMSMS ([Figure 1](#figure-1-blood-processing)):

#### Figure 1. Blood Processing
<img src="Fig1_blood.png" width="100%" height="auto">

<br>

The PEth assay followed these rules: as detailed in the sample data dictionary in [Table 2](#table-2-sample-data-dictionary-for-blood-peth), positive, negative, and canceled PEth tests result in corresponding scores of 1, 0, and 3 for sample-level (c_any_specimen_b). Continuous variables should be interpreted with caution based on the limits of quantification (LOQs) in [Table 1](#table-1-blood-assay-thresholds-peth). Class-level groupings for analyte screening and confirmatory tests are summarized in [Table 3](#table-3-mapping-from-class-to-screeners-and-confirmatory-tests-for-peth).

#### Table 1. Blood Assay Thresholds PEth
<table dir="ltr" border="1" cellspacing="0" cellpadding="0" data-sheets-root="1" data-sheets-baot="1"><colgroup><col width="151" /><col width="96" /><col width="100" /><col width="108" /><col width="134" /></colgroup>
<tbody>
	<tr>
		<td>Analyte</td>
		<td>LOD (ng/mL)</td>
		<td>LOQ (ng/mL)</td>
		<td>Cutoff (ng/mL)</td>
		<td>Detection Window</td>
	</tr>
	<tr>
		<td>Phosphatidylethanol</td>
		<td>4</td>
		<td>8</td>
		<td>20</td>
		<td>2-4 weeks</td>
	</tr>
</tbody>
</table>


#### Table 2. Sample Data Dictionary for Blood PEth
<table dir="ltr" border="1" cellspacing="0" cellpadding="0" data-sheets-root="1" data-sheets-baot="1"><colgroup><col width="151" /><col width="228" /><col width="88" /><col width="260" /></colgroup>
<tbody>
	<tr>
		<td>Variable</td>
		<td>Description</td>
		<td>Form</td>
		<td>Options</td>
	</tr>
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
		<td>c_ethanol_b</td>
		<td>Specimen level result<br />(direct confirmation)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: cancelled</td>
	</tr>
	<tr>
		<td>c_peth_b_cat</td>
		<td>Confirmatory only test in blood:<br />etoh metabolite<br />(categorical) (peth)</td>
		<td>Categorical</td>
		<td>1: positive<br />0: negative<br />3: cancelled</td>
	</tr>
	<tr>
		<td>c_peth_b</td>
		<td>Confirmatory test in blood:<br />etoh metabolite (peth)</td>
		<td>Continuous</td>
		<td>concentration value</td>
	</tr>
	<tr>
		<td>c_peth_unit_b</td>
		<td>Units</td>
		<td>String</td>
		<td>Units of measure</td>
	</tr>
</tbody>
</table>


#### Table 3. Mapping from Class to Screeners and Confirmatory Tests for PEth
<table dir="ltr" border="1" cellspacing="0" cellpadding="0" data-sheets-root="1" data-sheets-baot="1"><colgroup><col width="151" /><col width="96" /><col width="100" /><col width="108" /><col width="134" /></colgroup>
<tbody>
	<tr>
		<td>Class</td>
		<td>Confirmatory (only) Test</td>
	</tr>
	<tr>
		<td>Ethanol (c_ethanol_b)</td>
		<td>20phsphtdetbsp (c_peth_b_cat)</td>
	</tr>
</tbody>
</table>


## Quality Control & Known Issues
QC procedures involved examining assay ranges and categorical versus continuous measures. No common issues were identified from QC. No potential issues were flagged by subject matter experts.
