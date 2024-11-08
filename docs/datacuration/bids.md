# Overview: Brain Imaging Data Structure
As much as possible, HBCD processing utilizes the [Brain Imaging Data Structure](https://bids-specification.readthedocs.io/en/stable/) (BIDS) standard for data organization. At a high level, the HBCD BIDS structure will appear as follows:

```
assembly_bids/ 
|__ participants.tsv
|__ participants.json 
|__ sub-<label>/
|   |__ sub-<label>_sessions.tsv
|   |__ sub-<label>_sessions.json
|   |__ ses-<label>/
|       |__ anat/
|       |__ dwi/
|       |__ eeg/
|       |__ fmap/
|       |__ func/
|       |__ motion/
|       |__ mrs/
|       |__ sub-<label>_ses-<label>_scans.tsv
|       |__ sub-<label>_ses-<label>_scans.json
```
As expected in a large infant study, many subjects will have missing data elements, resulting in variations in the number of folders and files available for each subject and session. Additionally, the HBCD acquisition involves multiple modalities, some of which are collected at different times. Even within a single modality, certain acquisitions may occur on different days.

**Participant-Level Data**<br>
Participant-level data is stored in the `participants.tsv` file located in the root directory of the BIDS dataset. This file includes information on participants' sex. Descriptions of the column names and their properties are provided in the accompanying `participants.json` sidecar file.

**Session-Level Data**<br>
Session-level data is stored in the `sessions.tsv` file within the subject folder. This file provides details on the various sessions acquired for the participant, including the collection site, the participant’s age and gestational age at each session, and head size. Descriptions of the TSV column names and the properties of their values are available in the accompanying `sessions.json` sidecar file. *Note:* age measures are computed based on a birthdate measure that is jittered up to 7 days.

**Scan-Level Data**<br>
The complexity of data acquisition and the varying image quality across scans make the `scans.tsv` file, located in the session folder. This file contains information about how old the participant was at the time of the acquisition, and in certain cases there is also information about the quality of the underlying acquisition. To get a better understanding of what the different fields in the `scans.tsv` file mean, please refer to the `scans.json` file. *Note:* Age measures are computed based on a birthdate measure that is jittered up to 7 days.
