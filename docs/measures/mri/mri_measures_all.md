# Common Measure Details

## Implementation & Data Collection
**Method of Administration**: RA administered in person  
**Child Specific/Unspecific Form**: Child Specific  
**Visits**: 
**Estimated length of time for completion**:     

## Quality Control & Known Issues
**QC Procedures**        
Quality control of the MRI images can be found in the `scans.tsv` file in the session folder. The raw QC process involves reviewing unprocessed or lightly processed MRI data to identify and exclude data with severe artifacts from further processing. An initial protocol compliance check is performed by extracting information from DICOM headers and checking for common issues and protocol deviations, such as missing files or incorrect patient orientation. Automated QC metrics are calculated from the image data. A deep learning model estimates motion artifacts for structural scans (T1w, T2w, and qMRI), while metrics related to motion, bad frames, line artifacts, and FOV (field of view) cutoff are assessed for dMRI, fMRI, and field maps. A subset of series are selected for manual review based on multivariate prediction and Bayesian classifiers using the automated metrics. During the manual review, data quality is scored based on the severity of specific artifacts. For structural scans, motion artifacts are scored based on perceived severity on a scale of 0 to 3. Scores indicate no artifact (0), mild (1), moderate (2), or severe (3). Other artifacts, such as unusual intensity inhomogeneity or ghosting are noted by the reviewer. For dMRI, fMRI, and field maps, scored artifacts include susceptibility artifacts, FOV cutoff, and line artifacts. Other artifacts may be noted. Series with severe artifacts that clearly compromise data usability are rejected (QC=0). 

**Common Issues Identified**        


**Potential Issues**        


## Additional Information


## References
- Dean III, D. C., Tisdall, M. D., Wisnowski, J. L., Feczko, E., Gagoski, B., Alexander, A. L., ... & HBCD MRI Working Group. (2024). Quantifying brain development in the HEALthy Brain and Child Development (HBCD) Study: The magnetic resonance imaging and spectroscopy protocol. *Developmental Cognitive Neuroscience*, 70, 101452. [https://doi.org/10.1016/j.dcn.2024.101452](https://doi.org/10.1016/j.dcn.2024.101452)