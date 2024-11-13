# Motion Data Curation & BIDS Conversion

## BIDS Conversion
Axivity AX6 sensor data provided in the data release include `_motion.tsv` sensor recordings with corresponding `*_channels.tsv` files that describe each column of of the motion file. The acquisition (`acq-`) label for the calibration files is `calibration` while the label for the 72-hr data files is `primary`. The `task` label will be either `LeftLegMovement` or `RightLegMovement` for sensors placed on the left or right leg. Each `.tsv` file is accompanied by a JSON sidecar containing recording-related metadata: 

```
root/  
|__ participants.tsv  
|__ participants.json  
|__ sub-<label>/  
|   |__ sub-<label>_sessions.tsv  
|   |__ sub-<label>_sessions.json  
|   |__ ses-<label>/  
|       |__ sub-<label>_ses-<label>_scans.tsv  
|       |__ sub-<label>_ses-<label>_scans.json  
|       |__ motion/  
|       |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_motion.tsv  
|       |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_motion.json
|       |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_channels.tsv  
|       |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_channels.json
```
