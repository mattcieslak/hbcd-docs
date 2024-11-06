# UNDER CONSTRUCTION - Motion Data Curation & BIDS Conversion

## BIDS Conversion
Axivity AX6 sensor data provided in the data release include sensor recordings (`*_motion.tsv`) with corresponding `*_channels.tsv` files that describe each column of of the motion file. Each `.tsv` file is accompanied by a JSON sidecar containing recording-related metadata. BIDS entities represent the following:

|       BIDS Entity   |    Label      |   Description  |   
| ------------------  | ------------- | -----------------  |  
| `acq-<label>`       | `calibration` | calibration sensor file |  
| `acq-<label>`       | `primary` | 72-hr calibration file |  
| `task-<label>`       | `LeftLegMovement` | left leg sensor |  
| `task-<label>`       | `RightLegMovement` | right leg sensor |  
| `desc-<label>`       | `calibrated_recording-20` | sensor data (`*_motion.tsv`) calibrated<br>using tsv recording and resampled at 20 Hz |  
| `desc-<label>`       | `calibrated_recording-25` | sensor data (`*_motion.tsv`) calibrated<br>using tsv recording and resampled at 25 Hz |  

The resulting data structure:
```
root/  
|__ participants.tsv  
|__ participants.json  
|__ sub-<label>/  
|   |__ sub-<label>_sessions.tsv  
|   |__ sub-<label>_sessions.json  
|   |__ ses-<label>/  
|   |   |__ sub-<label>_ses-<label>_scans.tsv  
|   |   |__ sub-<label>_ses-<label>_scans.json  
|   |   |__ motion/  
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-calibration_motion.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-calibration_motion.json
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-calibration_channels.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-calibration_channels.json

|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-primary_motion.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-primary_motion.json
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-primary_channels.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<LeftLegMovement/RightLegMovement>_tracksys-imu_acq-primary_channels.json
```

## Detailed File Descriptions
Calibration file: `*_acq-calibration_channels.json`     
72-hour file: `*_acq-primary_channels.json`     
Description: The reference frame in which the channels of the Inertial Measurement Unit sensor used to prepare sensor calibration dataset is represented (left/right leg movement): Anterior, Right, Superior each corresponding to X, Y, and Z axis.

Calibration file: `*_acq-calibration_channels.tsv`     
72-hour file: `*_acq-primary_channels.tsv`     
Description: Includes measurement axis, sensor type, sensor position, unit, latency, and reference frame of each column in corresponding `*_motion.tsv` file   

Calibration file: `*_acq-calibration_motion.tsv`     
72-hour file: `*_acq-primary_motion.tsv`     
Description: Actual recording of the sensor (~ 1 minute) to prepare calibration dataset of the left/right leg movement sensor. There will be seven columns, and the detail about each column is in LL-Calib-Cahnnels-Details/RL-Calib-Channels-Details.

Calibration file: `*_acq-calibration_motion.json`     
72-hour file: `*_acq-primary_motion.json`     
Description: Recording related information: sampling frequency, effective sampling frequency, task name, task description, tracking system name, recording duration, accelerometer channel count, gyroscope channel count, latency channel count, manufacturer, sensor name, sensor’s serial number   

72-hour files: `*_desc-calibrated_recording-20_motion.tsv` and `*_desc-calibrated_recording-25_motion.tsv`
Description:  Movement sensor data calibrated using tsv recording and resampled at 20 Hz and 25 Hz respectively




