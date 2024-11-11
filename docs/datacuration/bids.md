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
In a large infant study, missing data is common, leading to variations in the number of folders and files available per subject and session. The HBCD acquisition spans multiple modalities, often collected at different times, with some acquisitions occurring on separate days even within the same modality. Participant-, session-, and scan-level data is captured by `participants.tsv`, `sessions.tsv`, and `scans.tsv` files respectively, each accompanied by JSON files with column descriptions and field definitions. Scan quality details can be found in `scans.tsv`.