# Wearable Sensors
**Full Name**: Infant leg movement data collected by wearable sensors.   
**Construct**: motor behavior, physical activity, sleep   

Wearable sensor data (accelerometer and gyroscope) were collected continuously across 72 hours from infants ankles to estimate how frequently and how vigorously an infant was moving and when the infant was asleep. Axivity AX6 sensors were placed on the infant's right and left ankles to record leg movements. Caregivers were advised to follow their usual routines but to remove the sensors if the infant went into water (e.g., a bathtub or pool) and replace them afterward. Before starting the 72-hour recording, each sensor was calibrated by capturing 10 seconds of data on each of its six flat surfaces. The sensors were set to continuously record accelerometer data (acceleration range of ±16 g) and gyroscope data (angular velocity range of ±2000 dps) at 25 samples per second. This data allows us to estimate the frequency and intensity of the infant's leg movements, including periods of sedentary, light, moderate-to-vigorous activity, or sleep. Please see [Pini et al. 2024](https://doi.org/10.1016/j.dcn.2024.101446) for a full description of this measure.   

<details>
<summary>Implementation & Data Collection Details</summary>
<ul>
<br>
<p><strong>Method of Administration</strong>: RA placed sensors on child at visit, sensors then worn while 72 hours of data were collected across typical activities in the natural environment. <br />
<strong>Visits</strong>: V02 (0-1 month) and V03 (3-8 months) </p>
</details>

<details>
<summary>References</summary>
<br>
<ul>
<li>Ghazi, M. A., Zhou, J., Havens, K. L., &amp; Smith, B. A. (2024). Accelerometer thresholds for estimating physical activity intensity levels in infants: A preliminary study. <em>Sensors</em> (Basel, Switzerland), 24(14), 4436. <a href="https://doi.org/10.3390/s24144436">https://doi.org/10.3390/s24144436</a></li>
<li>Jeung, S., Cockx, H., Appelhoff, S., Berg, T., Gramann, K., Grothkopp, S., Warmerdam, E., Hansen, C., Oostenveld, R., BIDS Maintainers, &amp; Welzel, J. (2024). Motion-BIDS: an extension to the brain imaging data structure to organize motion data for reproducible research. <em>Scientific Data</em>, 11(1), 716. <a href="https://doi.org/10.1038/s41597-024-03559-8">https://doi.org/10.1038/s41597-024-03559-8</a></li>
<li>Oh, J., Loeb, G. E., &amp; Smith, B. A. (2024). The utility of calibrating wearable sensors before quantifying infant leg movements. <em>Sensors</em> (Basel, Switzerland), 24(17), 5736. <a href="https://doi.org/10.3390/s24175736">https://doi.org/10.3390/s24175736</a></li>
<li>Oh, J., Ordoñez, E. L. T., Velasquez, E., Mejía, M., Del Pilar Grazioso, M., Rohloff, P., &amp; Smith, B. A. (2024). Associating neuromotor outcomes at 12 months with wearable sensor measures collected during early infancy in rural Guatemala. <em>Gait &amp; Posture</em>, 113, 477–489. <a href="https://doi.org/10.1016/j.gaitpost.2024.08.005">https://doi.org/10.1016/j.gaitpost.2024.08.005</a></li>
<li>Pini, N., Fifer, W. P., Oh, J., Nebeker, C., Croff, J. M., Smith, B. A., &amp; Novel Technology/Wearable Sensors Working Group. (2024). Remote data collection of infant activity and sleep patterns via wearable sensors in the HEALthy Brain and Child Development Study (HBCD). <em>Developmental Cognitive Neuroscience</em>, 69(101446), 101446. <a href="https://doi.org/10.1016/j.dcn.2024.101446">https://doi.org/10.1016/j.dcn.2024.101446</a></li>
<li>Smith, B. A., Trujillo-Priego, I. A., Lane, C. J., Finley, J. M., &amp; Horak, F. B. (2015). Daily quantity of infant leg movement: Wearable sensor algorithm and relationship to walking onset. <em>Sensors</em> (Basel, Switzerland), 15(8), 19006–19020. <a href="https://doi.org/10.3390/s150819006">https://doi.org/10.3390/s150819006</a></li>
<li>Trujillo-Priego, I. A., &amp; Smith, B. A. (2017). Kinematic characteristics of infant leg movements produced across a full day. <em>Journal of Rehabilitation and Assistive Technologies Engineering</em>, 4, 205566831771746. <a href="https://doi.org/10.1177/2055668317717461">https://doi.org/10.1177/2055668317717461</a></li>
<li>Trujillo-Priego, I. A., Zhou, J., Werner, I. F., Deng, W., &amp; Smith, B. A. (2020). Infant leg activity intensity before and after naps. <em>Journal for the Measurement of Physical Behaviour</em>, 3(2), 157–163.<a href="https://doi.org/10.1123/jmpb.2019-0011">https://doi.org/10.1123/jmpb.2019-0011</a></li>
</ul>
</details>
<br>

### Quality Control & Known Issues  
Raw calibration files were checked during active data collection to verify the presence of sufficient data for each of the six axes. A random selection of 72-hour data files were reviewed on a weekly basis to check for the presence of data, labeling of right and left leg, and sampling rate used. Since the QC process is manual and visual, only a small percentage of files were reviewed each week.

Quality control revealed that issues were generally rare and most data were deemed to be present and accurately collected. Errors that did arise were corrected when possible (though this was typically not feasible). 
<p>
<details>
<summary>Common QC Errors</summary>
</p>
<p>
<ul>
    <li>Calibration files:
        <ul>
            <li>Inadequate data for each of the six axes, often due to human error</li>
            <li>Missing data, caused by either human error or technical difficulties</li>
        </ul>
    </li>
    <li>72-hour files:
    <ul>
        <li>Missing data, due to human error, technical issues, or a parent/legal guardian declining to participate in this aspect of the study</li>
        <li>Sensors being removed for extended periods during the 72-hour collection</li>
        <li>Incorrect sampling rate</li>
    </ul>
</details>
</p>

No issues were flagged by subject matter experts, but users should note that accelerometer sensor timestamps can drift over time. Although right and left leg sensors start recording simultaneously with the same sampling rate and duration, exact time alignment cannot be assumed. By our estimates, Axivity AX6 sensors recording at 25 samples/sec diverge from one another by a couple of secondsover 72 hours, with the magnitude of this discrepancy increasing over time. Furthermore, offsets differed between sensors, necessitating a calibration procedure to correct for these differences (Oh et al., 2024).



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>REFERENCES</title>
  <style>
    .collapsible {
      background-color: #7cceb399;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
    }
    details {
      background-color: #7cceb366;
      padding: 10px;
      margin: 10px 1;
      border-radius: 5px;
    }
    summary {
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }
    a {
      color: #007BFF;
      text-decoration: none;
    }
  </style>
</html>