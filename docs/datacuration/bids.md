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
In a large infant study, missing data is common, leading to variations in the number of folders and files available per subject and session. The HBCD acquisition spans multiple modalities, often collected at different times, with some acquisitions occurring on separate days even within the same modality.

**Participant-Level Data**: Stored in `participants.tsv` in the dataset’s root directory, with column descriptions in the accompanying `participants.json`.

**Session-Level Data**: Located in `sessions.tsv` within each subject folder, detailing session-specific information such as collection site, participant’s age**, gestational age, and head size. Column properties are explained in `sessions.json`.

**Scan-Level Data**: Found in `scans.tsv` within the session folder, this file includes participant age** at acquisition and, in some cases, scan quality details. Field definitions are provided in `scans.json`.

<i>**Age measures are computed based on a birthdate measure that is jittered up to 7 days</i>