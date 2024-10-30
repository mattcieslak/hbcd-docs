---
hide:
  - toc
---

# Motion Data Curation & BIDS Conversion
Axivity AX6 sensors were used to record infant leg movements across 72 continuous hours. One sensor was placed on the distal right ankle and one sensor was placed on the distal left ankle, using leg warmers with a pocket to hold the sensor. Sensors were set to start recording at 10 am eastern/9 am central/8 am mountain/7 am pacific. Caregivers were instructed to go about their typical activities but to remove the sensors if the baby went into water (e.g., bathtub or pool) and replace them afterward.  
   
The sensors were set to record accelerometer (acceleration, range of +/- 16 g) and gyroscope (angular velocity, rate of rotation, +/- 2000 dps) data continuously at 25 samples per second. From this, it is possible to estimate how frequently and how vigorously an infant is moving his or her legs, including an estimate of sedentary physical activity, light physical activity, moderate-to-vigorous activity, or asleep.  
   
Before the 72 hours of data were collected, a calibration file was collected for each sensor. Instructions for collection of the calibration data were: “There are 6 flat surfaces of the sensor and we want to record data with the sensor sitting still on each of its flat surfaces. To do this: place the sensor on a level, flat surface (e.g., the surface of a desk or table). Wait 10 seconds. Rotate it so that it is resting on its next flat surface. Wait 10 seconds. You should put the sensor in 6 different positions and collect 10 seconds of data in each position, so just over a minute of data in total (including the time to rotate it). It does not matter what order you do this in. I like to get the 4 longer sides and then the 2 shorter ends. It does not have to be an exact 10 seconds in each position, counting “1-Mississippi, 2-Mississipi….10-Mississipi” will be close enough!”  
   
Data files included in the data release are raw sensor data in BIDS format for the calibration and 72-hour files for the right leg and the left leg, as well as files containing processed data outputs. All are described below in the “Additional Information” section.

Data structure for motion data:
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
|   |   |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_motion.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_motion.json  
|   |   |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_channels.tsv  
|   |   |   |__ sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_channels.json
```

## Sensor recordings
An actual recording will be labeled as `sub-<label>_ses-<label>_task-<label>_tracksys-imu_acq-<label>_motion.tsv`. The *acquisition* label for the calibration files is `calibration `while the label for the data files is `primary`. The task label will be either `LeftLegMovement` or `RightLegMovement`. The JSON sidecar contains recording related metadata `*_channels.tsv` which describes each column of the corresponding `*_motion.tsv`. 
