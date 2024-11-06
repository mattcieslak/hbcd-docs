Double check that this info is included in processing section

## Processed data outputs
**Full Name**: `sub-{dccid}_ses-{session number}_desc-kinematics_recording-20_motion.json`  
**Acronym/Brief Name**: Primary-Summary20  
**Description**: Summary kinematic measures based on the 72 hour leg movement data calibrated and resampled at 20Hz (LL-Primary-Recording-Calibrated20 & RL-Primary-Recording-Calibrated20). Measures include threshold values, movement rates, total movement counts, sleep times, average acceleration medians, peak acceleration medians, movement duration medians, and entropy values of the left and the right leg movement dataset.  
**Summary**: Summary kinematic variables from the movement dataset of both legs, calibrated and resampled at 20Hz.

**Full Name**: `sub-{dccid}_ses-{session number}_desc-kinematics_recording-25_motion.json`  
**Acronym/Brief Name**: Primary-Summary25  
**Description**: Summary kinematic measures based on the 72 hour leg movement data recorded at 25Hz and calibrated using LL-Primary-Recording-Calibrated25 and RL-Primary-Recording-Calibrated25. Measures include threshold values, movement rates, total movement counts, sleep times, average acceleration medians, peak acceleration medians, movement duration medians, and entropy values of the left and the right leg movement dataset.  
**Summary**: Summary kinematic variables from the movement dataset of both legs, calibrated.

**Full Name**: `sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_BOUTS.tsv`  
**Acronym/Brief Name**: PA-BOUTS  
**Description**: This file lists bouts of activity as they occur over time. There are 4 columns of data [start time of a bout, end time of a bout, duration of a bout, and classification of a bout]. The unit for time is seconds. The first line contains the headings, and the rest contain the data. Classification of bours is [0: sedentary, 3: light activity, 6: moderate-to-vigorous (MV) activity, 999: undefined (could not be computed)]. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A list of bouts of activity with timestamps and classification categories

**Full Name**: `sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_SUMMARY.json`  
**Acronym/Brief Name**: PA-SUMMARY  
**Description**: The overall summary of physical activity in terms of 3 different measures: counts (instances) recorded, in terms of percentage time spent, and in terms of actual time spent in minutes. For each measure, values will be listed for the total, sedentary, light, and moderate-to-vigorous (MV) activity. The fifth label, “undefined”, can be ignored. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: The overall summary of physical activity estimated from recording.

**Full Name**: `sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_RAW.json`  
**Acronym/Brief Name**: PA-RAW  
**Description**: The file lists instantaneous levels of activity as they occur over time. There are 2 columns of data, separated by commas: Unix epoch time (in seconds) at each instance, and classification at each instance. Classification of instance is [0: sedentary, 3: light activity, 6: moderate-to-vigorous (MV) activity, 999: undefined (could not be computed)]. {pa_side} and {pa_measure} are user defined. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A detailed description across time of when the infant was in different categories of physical activity

**Full Name**: `sub-{dccid}_ses-{session number}_leg-{pa_side*}_desc-{pa_measure*}PA_LOG.txt`  
**Acronym/Brief Name**: PA-LOG  
**Description**: The file lists the parameters provided to process data and generate *PA_RAW.json, *PA_SUMMARY.json, and *PA_BOUTS.tsv. In addition, the content of *PA_SUMMARY.json is available in this file. {pa_side} is ‘left’ or ‘right’, and {pa_measure} is ‘acceleration’ or ‘jerk’.  
**Summary**: A list of parameters used to estimate the physical activity categories and the summary of processing output.

**Full Name**: `PARAMETERS.json`  
**Acronym/Brief Name**: Kinematics-Param  
**Description**: The file lists the parameters provided when using the docker container (see page 3). Items include [bids_dir, output_dir, analytics_level, participant_label, session_id, interval, pa_measure, pa_side, entropy_type, entropy_measure]. Explanation of each item is available at **https://hbcd-motion-postproc.readthedocs.io/en/latest**.   
**Summary**: A list of parameters used to run the processing pipeline container.