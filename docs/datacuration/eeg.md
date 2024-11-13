# EEG Data Curation & BIDS Conversion

## BIDS Conversion
To facilitate data handling and preprocessing, we employ EEG2BIDS Wizard, a custom MATLAB application installed at all HBCD site used to upload the EEG files and associated metadata after each EEG session (see details in the section below). The resulting BIDS data structure is: 
```
assembly_bids/ 
|__ participants.tsv
|__ participants.json 
|__ sub-<label>/
|   |__ sub-<label>_sessions.tsv
|   |__ sub-<label>_sessions.json
|   |__ ses-<label>/
|       |__ eeg/
|       |

(Location of electrodes)
|       |   |__sub-<label>_ses-<label>_acq-ecg_space-CapTrak_electrodes.tsv
|       |   |__sub-<label>_ses-<label>_acq-ecg_space-CapTrak_coordsystem.json
|       |   |__sub-<label>_ses-<label>_acq-eeg_space-<CapTrak/CTF>_electrodes.tsv
|       |   |__sub-<label>_ses-<label>_acq-eeg_space-<CapTrak/CTF>_coordsystem.json

(Task acquisitions)
|       |   |__sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-<eeg/ecg>_channels.tsv
|       |   |__sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-<eeg/ecg>_eeg.json
|       |   |__sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-<eeg/ecg>_eeg.set
|       |   |__sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-<eeg/ecg>_events.tsv
|       |   |__sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-<eeg/ecg>_events.json
|       |   |
|       |   |__ sourcedata/
|       |       |__ sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-eeg_flags.json
|       |       |__ sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-eeg_impedances.json
|       |       |__ sub-<label>_ses-<label>_task-<FACE/MMN/RS/VEP>_acq-eeg_eventlogs.txt
```

**Location of electrodes**    
The EEG lead was placed on either the head (`acq-eeg`) or chest (`acq-ecg`). Location coordinates are specified in the `*_electrodes.tsv` file following cartesian coordinates specified by fields of the accompanying `*_coordsystem.json` file.

**Task acquisitions**      
EEG is acquired for each task (see [Data Measures & Quality Control > EEG](../measures/eeg/overview.md) for task descriptions) as indicated by the `task-<label>` BIDS entity

**Sourcedata files**    
These files include information about quality control (`*_flags.json`- see [Quality Control Checks](#quality-control-checks) below), impedance values to ensure good electrode contact (`*_impedence.json`), and task stimuli presentations (`*_eventlogs.txt`).

## EEG2BIDS Wizard Details
### Data Conversion
During EEG data acquisition, raw data are collected using Netstation acquisition software and stored in the form of .mff files. When data are uploaded to the Wizard, the initial step involves converting data from the native .mff file format to the .set format. The .set format is compatible with BIDS and necessary for subsequent EEG preprocessing with the HBCD-MADE pipeline.  

### Quality Control Checks
The application performs a series of quality control checks locally on the computer at each HBCD site to ensure the integrity and usability of the data. Results of these checks are immediately provided to the user. Quality control flags and acquisition notes are included in the sourcedata `*_flags.json` file. The checks include: 

   * Verification of event markers within the EEG data to ensure all required events are accurately recorded.  
   * Confirmation that the setup for stimulus presentation and EEG data acquisition adheres to the study protocol.  
   * Inspection of electrode impedances, ensuring that all values are within acceptable limits and properly assessed.  
   * Detection of multiple task runs and incomplete recordings.  
   * Verification of the use of correct E-Prime task versions.  

### Secure Data Transfer
Next, the EEG2BIDS Wizard facilitates the transfer of data to both a dedicated secure computing environment (SCE) housed at the University of Minnesota and to an Amazon Web Storage (ASW) S3 bucket.  

   * **SCE:** The Wizard handles the transfer of .mff files containing raw EEG, metadata, and personally identifiable information (PII) to the SCE. PII includes video recordings of the EEG session and photographs of EEG cap placement from multiple angles, which are used to rate quality of cap placement according to a rubric.  
   * **ASW S3 bucket:** A subset of data consisting of .set files, E-Prime stimuli files and associated non-PII metadata are uploaded to an AWS S3 bucket curated by the LORIS data management system where they are stored for subsequent processing and analysis. The contents of the ASW S3 bucket are represented on the EEG Quality Control dashboard, which is used by both study sites and the EEG Core team to access and monitor incoming EEG data.

After these operations are performed by the BIDS Wizard, data from the AWS S3 bucket are ingested into the CBRAIN supercomputer at the University of Minnesota where EEG preprocessing takes place. HBCD EEG data are preprocessed using the [HBCD-MADE pipeline](https://github.com/DCAN-Labs/HBCD-MADE). Information about the pipeline is available [here](https://docs-hbcd-made.readthedocs.io/en/latest/index.html). The outputs and derivatives generated during processing in CBRAIN are relayed to the LORIS interface which supports ongoing quality control and monitoring of incoming EEG data. 