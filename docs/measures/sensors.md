# Wearable Sensors
## Overview
**Full Name**: Infant leg movement data collected by wearable sensors.   
**Acronym/Brief Name**: N/A  
**Construct**: motor behavior, physical activity, sleep   
**Description**: Axivity AX6 sensors were used to record infant leg movements across 72 continuous hours. One sensor was placed on the distal right ankle and one sensor was placed on the distal left ankle, using legwarmers with a pocket to hold the sensor. Sensors were set to start recording at 10 am eastern/9 am central/8 am mountain/7 am pacific. Caregivers were instructed to go about their typical activities but to remove the sensors if the baby went into water (e.g., bathtub or pool) and replace them afterward.    
The sensors were set to record accelerometer (acceleration, range of +/- 16 g) and gyroscope (angular velocity, rate of rotation, +/- 2000 dps) data continuously at 25 samples per second. From this, we can estimate how frequently and how vigorously an infant is moving his or her legs, including an estimate of sedentary physical activity, light physical activity, moderate-to-vigorous activity, or asleep.    
Before the 72 hours of data were collected, a calibration file was collected for each sensor. Instructions for collection of the calibration data were:

> There are 6 flat surfaces of the sensor and we want to record data with the sensor sitting still on each if its flat surfaces. To do this: place the sensor on a level, flat surface (e.g., the surface of a desk or table). Wait 10 seconds. Rotate it so that it is resting on its next flat surface. Wait 10 seconds. You should put the sensor in 6 different positions and collect 10 seconds of data in each position, so just over a minute of data in total (including the time to rotate it). It does not matter what order you do this in. I like to get the 4 longer sides and then the 2 shorter ends. It does not have to be an exact 10 seconds in each position, counting “1-Mississippi, 2-Mississipi….10-Mississipi” will be close enough!

Data files included in the data release are raw sensor data in BIDS format for the calibration and 72-hour files for the right leg and the left leg, as well as files containing processed data outputs. All are described below in “Additional Information” section.

**Summary**: Wearable sensor data (accelerometer and gyroscope) were collected continuously across 72 hours from infants ankles to estimate how frequently and how vigorously an infant was moving and when the infant was asleep. 

## Implementation
**Method of Administration**: RA placed sensors on child at visit, sensors then worn while 72 hours of data were collected across typical activities in the natural environment.  
**REDCap Form Name**: N/A  
**Pilot Data Dictionary**: N/A  
**Spanish Translation**: N/A  
**Child Specific/Unspecific Form**: N/A  
**Respondent:** N/A

## Data Collection
**Visits Administered and corresponding age range of administration**: V02 (0-1 month of age) and V03 (3-8 months of age).  
**Estimated length of time for completion**: N/A

## Quality Control (QC)
**QC Procedures**   
Raw data files were spot-checked during the data collection time frame. Only a small percentage of data files were randomly checked each week as the process was manual and visual. When checked, calibration files were checked for presence of adequate data for each of 6 axes and 72-hour files were checked for the presence of data, labeling of right and left leg, and sampling rate used.

**Common Issues Identified**    
Common issues identified during QC processes included inadequate data for each of the 6 axes in calibration files (human error), missing data for calibration files (due to human error or technical difficulties), missing data for 72 hours (due to human error, technical difficulties, or parent/legal guardian declining to participate in this aspect of the study), sensors being removed for prolonged periods during the 72 hours, or incorrect sampling rate used during the 72 hour collection. If possible, errors were corrected (but this was not often possible). All issued occurred rarely overall and the majority of the data were judged to be present and correctly collected.

## Potential Issues Flagged by Subject Matter Experts
No issues were found. Users are reminded that accelerometer sensor timestamps drift over time, so even though the right and left leg sensors started recording at the same time and recorded for the same duration of time at the same sampling rate, one cannot assume that the time specified matches exactly between the 2 sensors. By our estimates, Axivity AX6 sensors recording at 25 samples/sec diverge from one another by a couple of seconds by the end of 72 hours, and the magnitude of this error increases over time. Further, offsets were different between different sensors, so a calibration procedure was used to adjust for this. See Oh, J., Loeb, G. E., & Smith, B. A. (2024). The Utility of Calibrating Wearable Sensors before Quantifying Infant Leg Movements. *Sensors*, *24*(17), 5736

## Additional Information
Data files included in the data release are raw sensor data in BIDS format for the calibration and 72-hour files for the right leg and the left leg, as well as files containing processed data outputs.

### Raw data, calibration files
**Full Name:** sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_channels.json  
**Acronym/Brief Name**: LL-Calib-Channels-Ref  
**Description**: The reference frame in which the channels of the Inertial Measurement Unit sensor used to prepare sensor calibration dataset is represented (left leg movement): Anterior, Right, Superior each corresponding to X, Y, and Z axis.

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-calibration_channels.json  
**Acronym/Brief Name**: RL-Calib-Channels-Ref  
**Description**: The reference frame in which the channels of the Inertial Measurement Unit sensor used to prepare sensor calibration dataset is represented (right leg movement): Anterior, Right, Superior each corresponding to X, Y, and Z axis.  
**Summary**: Reference frame of the IMU sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_channels.tsv  
**Acronym/Brief Name**: LL-Calib-Channels-Details  
**Description**: Measurement axis, sensor type, sensor position, unit, latency, reference frame of each column in sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_motion.tsv   
**Summary**: Details about the columns of the left leg calibration dataset.

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-calibration_channels.tsv  
**Acronym/Brief Name**: RL-Calib-Channels-Details  
**Description**: Measurement axis, sensor type, sensor position, unit, latency, reference frame of each column in sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-calibration_motion.tsv   
**Summary**: Details about the columns of the right leg calibration dataset.

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_motion.tsv  
**Acronym/Brief Name**: LL-Calib-Recording  
**Description**: Actual recording of the sensor (~ 1 minute) to prepare calibration dataset of the left leg movement sensor. There will be seven columns, and the detail about each column is in LL-Calib-Cahnnels-Details.   
**Summary**: Calibration dataset, left leg movement sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-calibration_motion.tsv  
**Acronym/Brief Name**: RL-Calib-Recording  
**Description**: Actual recording of the sensor (~ 1 minute) to prepare calibration dataset of the right leg movement sensor. There will be seven columns, and the detail about each column is in RL-Calib-Channels-Details.  
**Summary**: Calibration dataset, right leg movement sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_motion.json  
**Acronym/Brief Name**: LL-Calib-Recording-Details  
**Description**: Recording related information: sampling frequency, effective sampling frequency, task name, task description, tracking system name, recording duration, accelerometer channel count, gyroscope channel count, latency channel count, manufacturer, sensor name, sensor’s serial number   
**Summary**: Calibration dataset of the left leg movement sensor related information

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-calibration_motion.json  
**Acronym/Brief Name**: RL-Calib-Recording-Details  
**Description**: Recording related information: sampling frequency, effective sampling frequency, task name, task description, tracking system name, recording duration, accelerometer channel count, gyroscope channel count, latency channel count, manufacturer, sensor name, sensor’s serial number   
**Summary**: Calibration dataset of the right leg movement sensor related information

### Raw data, 72-hour files
**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-primary_channels.json  
**Acronym/Brief Name**: LL-Primary-Channels-Ref  
**Description**: The reference frame in which the channels of the Inertial Measurement Unit sensor used to prepare sensor movement dataset is represented (left leg movement): Anterior, Right, Superior each corresponding to X, Y, and Z axis   
**Summary**: Reference frame of the IMU sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-primary_channels.json  
**Acronym/Brief Name**: RL-Primary-Channels-Ref  
**Description**: The reference frame in which the channels of the Inertial Measurement Unit sensor used to prepare sensor movement dataset is represented (right leg movement): Anterior, Right, Superior each corresponding to X, Y, and Z axis   
**Summary**: Reference frame of the IMU sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-calibration_channels.tsv  
**Acronym/Brief Name**: LL-Primary-Channels-Details  
**Description**: Measurement axis, sensor type, sensor position, unit, latency, reference frame of each column in sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-primary_motion.tsv   
**Summary**: Details about the columns of the left leg movement dataset.

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-primary_channels.tsv  
**Acronym/Brief Name**: RL-Primary-Channels-Details  
**Description**: Measurement axis, sensor type, sensor position, unit, latency, reference frame of each column in sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-primary_motion.tsv   
**Summary**: Details about the columns of the right leg movement dataset.

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-primary_motion.tsv  
**Acronym/Brief Name**: LL-Primary-Recording  
**Description**: Actual recording of the sensor (~ 1 minute) to prepare movement dataset of the left leg movement sensor. There will be seven columns, and the detail about each column is in LL-Primary-Channels-Details.  
**Summary**: Movement dataset, left leg movement sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-primary_motion.tsv  
**Acronym/Brief Name**: RL-Primary-Recording  
**Description**: Actual recording of the sensor (~ 1 minute) to prepare movement dataset of the right leg movement sensor. There will be seven columns, and the detail about each column is in RL-Calib-Channels-Details.  
**Summary**: Movement dataset, right leg movement sensor

**Full Name**: sub-{dccid}_ses-{session number}_task-LeftLegMovement_tracksys-imu_acq-primary_motion.json  
**Acronym/Brief Name**: LL-Primary-Recording-Details  
**Description**: Recording related information: sampling frequency, effective sampling frequency, task name, task description, tracking system name, recording duration, accelerometer channel count, gyroscope channel count, latency channel count, manufacturer, sensor name, sensor’s serial number   
**Summary**: Movement dataset of the left leg movement sensor related information

**Full Name**: sub-{dccid}_ses-{session number}_task-RightLegMovement_tracksys-imu_acq-primary_motion.json  
**Acronym/Brief Name**: RL-Primary-Recording-Details  
**Description**: Recording related information: sampling frequency, effective sampling frequency, task name, task description, tracking system name, recording duration, accelerometer channel count, gyroscope channel count, latency channel count, manufacturer, sensor name, sensor’s serial number   
**Summary**: Movement dataset of the right leg movement sensor related information

**Full Name**: sub-{dccid}_ses-{session number}_leg-left_desc-calibrated_recording-20_motion.tsv  
**Acronym/Brief Name**: LL-Primary-Recording-Calibrated20  
**Description**: 72 hour left leg movement data calibrated using LL-Calib-Recording and resampled at 20 Hz.   
**Summary**: Movement dataset of the left leg movement sensor calibrated and resampled at 20 Hz.

**Full Name**: sub-{dccid}_ses-{session number}_leg-right_desc-calibrated_recording-20_motion.tsv  
**Acronym/Brief Name**: RL-Primary-Recording-Calibrated20  
**Description**: 72 hour right leg movement data calibrated using RL-Calib-Recording and resampled at 20 Hz.   
**Summary**: Movement dataset of the right leg movement sensor calibrated and resampled at 20 Hz.

**Full Name**: sub-{dccid}_ses-{session number}_leg-left_desc-calibrated_recording-25_motion.tsv  
**Acronym/Brief Name**: LL-Primary-Recording-Calibrated25  
**Description**: 72 hour left leg movement data calibrated using LL-Calib-Recording. 25 Hz is the original sampling rate.  
**Summary**: Movement dataset of the left leg movement sensor, calibrated.

**Full Name**: sub-{dccid}_ses-{session number}_leg-right_desc-calibrated_recording-25_motion.tsv  
**Acronym/Brief Name**: RL-Primary-Recording-Calibrated25  
**Description**: 72 hour right leg movement data calibrated using RL-Calib-Recording. 25 Hz is the original sampling rate.  
**Summary**: Movement dataset of the right leg movement sensor, calibrated

### Processed data outputs
**Full Name**: sub-{dccid}_ses-{session number}_desc-kinematics_recording-20_motion.json  
**Acronym/Brief Name**: Primary-Summary20  
**Description**: Summary kinematic measures based on the 72 hour leg movement data calibrated and resampled at 20Hz (LL-Primary-Recording-Calibrated20 & RL-Primary-Recording-Calibrated20). Measures include threshold values, movement rates, total movement counts, sleep times, average acceleration medians, peak acceleration medians, movement duration medians, and entropy values of the left and the right leg movement dataset.  
**Summary**: Summary kinematic variables from the movement dataset of both legs, calibrated and resampled at 20Hz.

**Full Name**: sub-{dccid}_ses-{session number}_desc-kinematics_recording-25_motion.json  
**Acronym/Brief Name**: Primary-Summary25  
**Description**: Summary kinematic measures based on the 72 hour leg movement data recorded at 25Hz and calibrated using LL-Primary-Recording-Calibrated25 and RL-Primary-Recording-Calibrated25. Measures include threshold values, movement rates, total movement counts, sleep times, average acceleration medians, peak acceleration medians, movement duration medians, and entropy values of the left and the right leg movement dataset.  
**Summary**: Summary kinematic variables from the movement dataset of both legs, calibrated.

**Full Name**: sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_BOUTS.tsv  
**Acronym/Brief Name**: PA-BOUTS  
**Description**: This file lists bouts of activity as they occur over time. There are 4 columns of data [start time of a bout, end time of a bout, duration of a bout, and classification of a bout]. The unit for time is seconds. The first line contains the headings, and the rest contain the data. Classification of bours is [0: sedentary, 3: light activity, 6: moderate-to-vigorous (MV) activity, 999: undefined (could not be computed)]. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A list of bouts of activity with timestamps and classification categories

**Full Name**: sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_SUMMARY.json  
**Acronym/Brief Name**: PA-SUMMARY  
**Description**: The overall summary of physical activity in terms of 3 different measures: counts (instances) recorded, in terms of percentage time spent, and in terms of actual time spent in minutes. For each measure, values will be listed for the total, sedentary, light, and moderate-to-vigorous (MV) activity. The fifth label, “undefined”, can be ignored. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: The overall summary of physical activity estimated from recording.

**Full Name**: sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_RAW.json  
**Acronym/Brief Name**: PA-RAW  
**Description**: The file lists instantaneous levels of activity as they occur over time. There are 2 columns of data, separated by commas: Unix epoch time (in seconds) at each instance, and classification at each instance. Classification of instance is [0: sedentary, 3: light activity, 6: moderate-to-vigorous (MV) activity, 999: undefined (could not be computed)]. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A detailed description across time of when the infant was in different categories of physical activity

**Full Name**: sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_LOG.txt  
**Acronym/Brief Name**: PA-LOG  
**Description**: The file lists the parameters provided to process data and generate *PA_RAW.json, *PA_SUMMARY.json, and *PA_BOUTS.tsv. In addition, the content of *PA_SUMMARY.json is available in this file. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A list of parameters used to estimate the physical activity categories and the summary of processing output.

**Full Name**: PARAMETERS.json  
**Acronym/Brief Name**: Kinematics-Param  
**Description**: The file lists the parameters provided when using the docker container (see page 3). Items include [bids_dir, output_dir, analytics_level, participant_label, session_id, interval, pa_measure, pa_side, entropy_type, entropy_measure]. Explanation of each item is available at **https://hbcd-motion-postproc.readthedocs.io/en/latest**.  

- bids_dir: the path to the BIDS directory of the study (same for all subjects)
- output_dir: the path to the folder where outputs will be saved  
- analysis_level: always be ‘participant’  
- participant_label: the name/label of the subject to be processed  
- session_id: the name of a specific session to be processed  
- interval: the label to correct or not correct the uneven sampling interval (‘raw’ or ‘corrected’)  
- pa_measure: which measure to estimate the physical activity categories (‘acceleration’ or ‘jerk’)  
- pa_side: which leg to estimate the physical activity categories (‘Left/L’ or ‘Right/R’)  
- entropy_type: entropy type (‘SampEn’ for sample entropy and ‘FuzzEn’ for fuzzy entropy)  
- entropy_measure: kinematic variable for which to calculate entropy (‘avgacc’ for the average acceleration per leg movement and ‘pkacc’ for the peak acceleration per leg movement)  

**Summary**: A list of parameters used to run the processing pipeline container.

## References
*Describing the protocol decision-making process.* Pini N, Fifer WP, Oh J, et al. Remote Data Collection of Infant Activity and Sleep Patterns via Wearable Sensors in the HEALthy Brain and Child Development Study (HBCD). *Dev Cogn Neurosci*. 2024;69:101446. doi:10.1016/j.dcn.2024.101446    

*BIDS format for raw data files.* Jeung, S., Cockx, H., Appelhoff, S., Berg, T., Gramann, K., Grothkopp, S., ... & Welzel, J. (2024). Motion-BIDS: an extension to the brain imaging data structure to organize motion data for reproducible research. *Scientific Data*, *11*(1), 716.  

*Calibration process to prepare data for calculation of infant leg movement characteristics*. Oh, J., Loeb, G. E., & Smith, B. A. (2024). The Utility of Calibrating Wearable Sensors before Quantifying Infant Leg Movements. *Sensors*, *24*(17), 5736.  

*Algorithms to identify infant leg movement characteristics*. Smith, B. A., Trujillo-Priego, I. A., Lane, C. J., Finley, J. M., & Horak, F. B. (2015). Daily quantity of infant leg movement: Wearable sensor algorithm and relationship to walking onset. *Sensors*, *15*(8), 19006-19020. Trujillo-Priego IA, Smith BA. Kinematic characteristics of infant leg movements produced across a full day. *Journal of rehabilitation and assistive technologies engineering*. 2017;4:205566831771746. doi:10.1177/2055668317717461. Trujillo-Priego IA, Zhou J, Werner IF, Deng W, Smith BA. Infant Leg Activity Intensity Before and After Naps. Journal for the Measurement of Physical Behaviour. 2020;3(2):157-163. doi:10.1123/jmpb.2019-0011. Oh J, Ordoñez ELT, Velasquez E, et al. Associating neuromotor outcomes at 12 months with wearable sensor measures collected during early infancy in rural Guatemala. *Gait Posture*. Published online 2024. doi:10.1016/j.gaitpost.2024.08.005.   

*Algorithm to estimate intensity of infant physical activity.* Ghazi, M. A., Zhou, J., Havens, K. L., & Smith, B. A. (2024). Accelerometer Thresholds for Estimating Physical Activity Intensity Levels in Infants: A Preliminary Study. *Sensors*, *24*(14), 4436.  

**Processing code** used to obtain processed data outputs are available as a container on [INC Laboratory's Docker Hub](https://hub.docker.com/r/inclab/hbcd_motion_postproc) (source code available on GitHub [here](https://github.com/Infant-Neuromotor-Control-Lab/hbcd_motion_postproc))

# Infant Sensor Questionnaire
## Overview
**Full Name**: Daily survey about infant heart rate sensor and infant leg movement sensors.   
**Acronym/Brief Name**: Infant Sensor Questionnaire  
**Construct**: motor behavior, physical activity, sleep   
**Description**: Survey was sent to primary caregiver once per day for 3 days during the 72 hour data collection of infant heart rate sensor data and infant leg movement sensor data. Surveys were automatically sent via email or text message (per caregiver preference) at 10 am eastern/9 am central/8 am mountain/7 am pacific. The surveys were sent after the sensors had been recording for 24, 48, and 72 hours. The survey asked about the preceding 24-hour period. It asked whether the sensors were worn for most of the time and about the daily activities of the infant (whether or not it was a fairly typical 24 hours for the infant, estimates of how much they napped and slept, how much they were in a car seat, swing or other restraining device, how much they were in a moving car or stroller or being carried, and whether or not their legs are swaddled during naps and sleep). This survey was created by the workgroup.
**Summary**: The questionnaire was sent once per day for 3 days while the infant was wearing the heart rate sensor and infant leg movement sensors to obtain information about context of the sensor recordings.

## Implementation
**Method of Administration**: RA marked preferred contact and preferred method of contact (email or text message) at visit, then surveys were sent automatically.  
**REDCap Form Name**: sens_ch_rcpt  
**Pilot Data Dictionary**: nt_ch_sens_i_qtn_1, nt_ch_sens_i_qtn_2, nt_ch_sens_i_qtn_3  
**Spanish Translation**: Yes, done by study  
**Child Specific/Unspecific Form**: Caregiver answering questions about their child.  
**Respondent:** Caregiver

## Data Collection
**Visits Administered and corresponding age range of administration**: V02 (0-1 month of age) and V03 (3-8 months of age).  
**Estimated length of time for completion**: N/A

## Quality Control (QC)
**QC Procedures**   
Surveys were spot-checked during the data collection time frame. Only a small percentage of surveys were randomly checked each week as the process was manual. When checked, surveys were checked for the presence of responses. When no responses were provided, RA’s were contacted to confirm whether or not surveys had gone out to the participants as intended.  
**Common Issues Identified**    
Common issues identified during QC processes included surveys that had no responses. Sometimes this was human error (preferred contact or preferred method of communication not selected by RA) or potentially technological malfunction, and sometimes it was caregiver non-response. Caregiver non-response was the reason for the majority of the surveys without responses. Caregiver non-response was common.

## Potential Issues Flagged by Subject Matter Experts
None
