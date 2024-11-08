# EEG Data Curation & BIDS Conversion
EEG data is converted from MFF to SET using a custom MATLAB script and application. This script produces flags to evaluate the acquisition quality according to the protocol guidelines. Data is collected as raw .mff files outputted from the MagStim EGI Netstation application. Next, the EEG2Bids Wizard application converts raw .mff structured files to eeg .set files, and then adds the .set files into a standardized BIDS formatted folder. This final folder is uploaded to the Loris dashboard and any personally identifiable information is extracted to a secure computing environment in the UMN server. Quality control flags and acquisition notes can be found in the `sourcedata/*_flags.json` file shown below.

**TO DO: COMPLETE TREE**
```
assembly_bids/ 
|__ participants.tsv
|__ participants.json 
|__ sub-<label>/
|   |__ sub-<label>_sessions.tsv
|   |__ sub-<label>_sessions.json
|   |__ ses-<label>/
|       |__ eeg/
|       |   |__ EEG FILE.nii.gz
|       |   |__ EEG FILE.json
|       |   |__ sourcedata/
|       |       |__ sub-<label>_ses-<label>_acq-eeg_flags.json
```