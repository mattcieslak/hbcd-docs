# Wearable Sensors
## Measure Overview
**Full Name**: Infant leg movement data collected by wearable sensors.   
**Construct**: motor behavior, physical activity, sleep   

**Description**     
Please see [Pini et al. 2024](https://doi.org/10.1016/j.dcn.2024.101446) for a full description of this measure. In brief, Axivity AX6 sensors were placed on the infant's right and left ankles to record leg movements over 72 continuous hours. Caregivers were advised to follow their usual routines but to remove the sensors if the infant went into water (e.g., a bathtub or pool) and replace them afterward. Before starting the 72-hour recording, each sensor was calibrated by capturing 10 seconds of data on each of its six flat surfaces. The sensors were set to continuously record accelerometer data (acceleration range of ±16 g) and gyroscope data (angular velocity range of ±2000 dps) at 25 samples per second. This data allows us to estimate the frequency and intensity of the infant's leg movements, including periods of sedentary, light, moderate-to-vigorous activity, or sleep. 

**Summary**     
Wearable sensor data (accelerometer and gyroscope) were collected continuously across 72 hours from infants ankles to estimate how frequently and how vigorously an infant was moving and when the infant was asleep. 

## Implementation & Data Collection
**Method of Administration**: RA placed sensors on child at visit, sensors then worn while 72 hours of data were collected across typical activities in the natural environment.    
**Visits**: V02 (0-1 months) and V03 (3-8 months)  

## Quality Control & Known Issues
**QC Procedures**   
Raw calibration files were checked during active data collection to verify the presence of sufficient data for each of the six axes. A random selection of 72-hour data files were reviewed on a weekly basis to check for the presence of data, labeling of right and left leg, and sampling rate used. Since the QC process is manual and visual, only a small percentage of files were reviewed each week.

**Common Issues Identified**    
Quality control (QC) revealed that issues were generally rare, and most data were deemed to be present and accurately collected. However, when errors did occur, they most commonly involved:

- Calibration files:
    - Inadequate data for each of the six axes, often due to human error
    - Missing data, caused by either human error or technical difficulties

- 72-hour files:
    - Missing data, due to human error, technical issues, or a parent/legal guardian declining to participate in this aspect of the study
    - Sensors being removed for extended periods during the 72-hour collection
    - Incorrect sampling rate

Where possible, errors were corrected, though this was often not feasible

**Potential Issues**  
No issues were flagged by subject matter experts, but users should note that accelerometer sensor timestamps can drift over time. Although right and left leg sensors start recording simultaneously with the same sampling rate and duration, exact time alignment cannot be assumed. By our estimates, Axivity AX6 sensors recording at 25 samples/sec diverge from one another by a couple of secondsover 72 hours, with the magnitude of this discrepancy increasing over time. Furthermore, offsets differed between sensors, necessitating a calibration procedure to correct for these differences (Oh et al., 2024).

## References
- Ghazi, M. A., Zhou, J., Havens, K. L., & Smith, B. A. (2024). Accelerometer thresholds for estimating physical activity intensity levels in infants: A preliminary study. *Sensors* (Basel, Switzerland), 24(14), 4436. [https://doi.org/10.3390/s24144436](https://doi.org/10.3390/s24144436)
- Jeung, S., Cockx, H., Appelhoff, S., Berg, T., Gramann, K., Grothkopp, S., Warmerdam, E., Hansen, C., Oostenveld, R., BIDS Maintainers, & Welzel, J. (2024). Motion-BIDS: an extension to the brain imaging data structure to organize motion data for reproducible research. *Scientific Data*, 11(1), 716. [https://doi.org/10.1038/s41597-024-03559-8](https://doi.org/10.1038/s41597-024-03559-8)
- Oh, J., Loeb, G. E., & Smith, B. A. (2024). The utility of calibrating wearable sensors before quantifying infant leg movements. *Sensors* (Basel, Switzerland), 24(17), 5736. [https://doi.org/10.3390/s24175736](https://doi.org/10.3390/s24175736)
- Oh, J., Ordoñez, E. L. T., Velasquez, E., Mejía, M., Del Pilar Grazioso, M., Rohloff, P., & Smith, B. A. (2024). Associating neuromotor outcomes at 12 months with wearable sensor measures collected during early infancy in rural Guatemala. *Gait & Posture*, 113, 477–489. [https://doi.org/10.1016/j.gaitpost.2024.08.005](https://doi.org/10.1016/j.gaitpost.2024.08.005)
- Pini, N., Fifer, W. P., Oh, J., Nebeker, C., Croff, J. M., Smith, B. A., & Novel Technology/Wearable Sensors Working Group. (2024). Remote data collection of infant activity and sleep patterns via wearable sensors in the HEALthy Brain and Child Development Study (HBCD). *Developmental Cognitive Neuroscience*, 69(101446), 101446. [https://doi.org/10.1016/j.dcn.2024.101446](https://doi.org/10.1016/j.dcn.2024.101446)
- Smith, B. A., Trujillo-Priego, I. A., Lane, C. J., Finley, J. M., & Horak, F. B. (2015). Daily quantity of infant leg movement: Wearable sensor algorithm and relationship to walking onset. *Sensors* (Basel, Switzerland), 15(8), 19006–19020. [https://doi.org/10.3390/s150819006](https://doi.org/10.3390/s150819006)
- Trujillo-Priego, I. A., & Smith, B. A. (2017). Kinematic characteristics of infant leg movements produced across a full day. *Journal of Rehabilitation and Assistive Technologies Engineering*, 4, 205566831771746. [https://doi.org/10.1177/2055668317717461](https://doi.org/10.1177/2055668317717461)
- Trujillo-Priego, I. A., Zhou, J., Werner, I. F., Deng, W., & Smith, B. A. (2020). Infant leg activity intensity before and after naps. *Journal for the Measurement of Physical Behaviour*, 3(2), 157–163.[https://doi.org/10.1123/jmpb.2019-0011](https://doi.org/10.1123/jmpb.2019-0011)