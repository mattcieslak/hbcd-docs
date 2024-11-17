# Quantitative MRI
## QALAS
**Full Name**: The five QALAS volumes   
**Acronym/Brief Names**: qMRI, QALAS        
**Construct**: MRI acquisition      

The QALAS sequence provides five brain volumes, based on turbo-flash readouts, with different T2 and T1 weightings, from which T1, T2 and PD maps are estimated. The first readout / echo train is preceded by a T2-preparation volume providing T2 weighting. After the first echo train, an inversion pulse is played, which imposes T1 weighting on the remaining 4 echo trains. See the schematic of the pulse sequence diagram below. Using these two magnetization preparations, one is then able to estimate quantitative T1, T2 and PD maps from the five acquired volumes. The estimated length of time for completion is ~5min on Siemens scanners and ~4 mins on GE and Philips scanners. 

**Figure 1. Rough schematic of the pulse sequence diagram of the QALAS acquisition, accompanied with representative images from each of the five acquired volumes (figure courtesy of Fujita et al, 2024)**
![](qalas_Fig1.png)

### Quality Control & Known Issues
QC procedures include visual inspection of the image quality of the 3rd and 4th acquired volume (depending on the age of the baby), which should resemble the tissue contrast of a T1-weighting (MPRAGE) scan. One common QC issue noted as that different sites might have different criteria for what a motion-degraded QALAS scan looks like. No potential issues were flagged by subject matter experts.

<details class="collapsible references">
  <summary class="references" style="font-size: 1.2em; margin: 0 0 5x;">References</summary>
 <ul>
    <li>Fujita, S., Gagoski, B., Hwang, K.-P., Hagiwara, A., Warntjes, M., Fukunaga, I., Uchida, W., Saito, Y., Sekine, T., Tachibana, R., Muroi, T., Akatsu, T., Kasahara, A., Sato, R., Ueyama, T., Andica, C., Kamagata, K., Amemiya, S., Takao, H., … Aoki, S. (2024). Cross-vendor multiparametric mapping of the human brain using 3D-QALAS: A multicenter and multivendor study. <i>Magnetic Resonance in Medicine</i>, 91(5), 1863–1875. <a href="https://doi.org/10.1002/mrm.29939" target="_blank">https://doi.org/10.1002/mrm.29939</a></li>
    <li>Kvernby, S., Warntjes, M. J. B., Haraldsson, H., Carlhäll, C.-J., Engvall, J., & Ebbers, T. (2014). Simultaneous three-dimensional myocardial T1 and T2 mapping in one breath hold with 3D-QALAS. <i>Journal of Cardiovascular Magnetic Resonance: Official Journal of the Society for Cardiovascular Magnetic Resonance</i>, 16(1), 102. <a href="https://doi.org/10.1186/s12968-014-0102-0" target="_blank">https://doi.org/10.1186/s12968-014-0102-0</a></li>
  </ul>
</details>

## B1 Fieldmap
**Full Name**: Transmit radiofrequency field map        
**Acronym/Brief Name**: B1+ map         
**Construct**: MRI acquisition   

The HBCD MRI protocol includes a short MRI acquisition (<1min) to measure the B1+ field. B1+ maps are used to calibrate the flip angle measurements required for accurate and reliable estimation of the T1, T2 and PD maps from the QALAS images. Ideally, the flip angle that is prescribed on the MRI scanner would be uniform across the entire imaging volume. However, due to variations and inhomogeneities in the B1+ field, the prescribed flip angle can vary across the imaging volume. The B1+ map represents this spatially-varying field over the image and can be used to calibrate flip angle measurements. Since the transmit, B1+ field is spatially smooth and slowly varying, course resolutions of these scans are acceptable, which result in fast acquisition times. There are many different methods that measure the B1+ fields, and the MRI vendors have different ones readily available on their platform. For the purposes of our MRI protocol, on the GE and Philips scanner, the actual flip angle (AFI) method was used (Yarnykh VL, 2007), whereas on the Siemens scanner, the pre-saturation turbo-flash-readout sequence was used. The duration of these acquisitions were ~30-45s for all three types of scanner vendors (Siemens, GE, Philips). 

### Quality Control & Known Issues
QC procedures include visual inspection of the image quality of the acquired magnitude images. Different sites might have different criteria for what a motion degraded B1+ mapping scan looks like. 

<details class="collapsible references">
  <summary class="references" style="font-size: 1.2em; margin: 0 0 5x;">References</summary>
  <ul>
    <li>Fautz H-P, Vogel M, Gross P, Kerr A, Zhu Y. B1 mapping of coil arrays for parallel transmission. <i>Proceedings of the 16th Annual Meeting of ISMRM</i>, Toronto, Canada. Vol. 1247. 2008.</li>
    <li>Yarnykh, V. L. (2007). Actual flip-angle imaging in the pulsed steady state: a method for rapid three-dimensional mapping of the transmitted radiofrequency field. <i>Magnetic Resonance in Medicine</i>, 57(1), 192–200. <a href="https://doi.org/10.1002/mrm.21120" target="_blank">https://doi.org/10.1002/mrm.21120</a></li>
  </ul>
</details>

## T1, T2, & PD 
**Full Name**: Longitudinal relaxation time (T1), Transverse Relaxation Time (T2) and Proton Density (PD) maps      
**Acronym/Brief Names**: T1, T2, & PD        
**Construct**: Processing   

Quantitative parametric maps of T1, T2, and PD are sensitive to underlying neurobiological mechanisms, including water content, iron deposition and myelination. The HBCD MRI protocol utilizes the 3D-QALAS technique to provide estimates of T1, T2, and PD.

The MRI tissue contrast arises primarily from differences in the longitudinal (T1) and transverse (T2) relaxation times. Conventional clinical and research neuroimaging techniques have been disproportionately represented by qualitative relaxation time weighted brain images (e.g., T1w, T2w scans). While we include these traditional structural scans in the HBCD protocol, they are a complex function of underlying relaxation properties, pulse sequence parameters, and other participant- and hardware-specific effects, such as participant position. The dependency of the MR signal on these extraneous sources limits interpretation and one’s ability to associate observed contrast changes to biological mechanisms. Consequently, quantitative comparison across participants, longitudinal sessions, and multiple sites becomes difficult. This is especially relevant in pediatric neuroimaging, where the brain is undergoing rapid development that results in changing free water distribution, iron content, and brain myelination. As a result, contrast in conventional MRI changes as a function of age, complicating the study of pediatric populations across varying age ranges. Direct measurement of these relaxation properties can overcome many of these limitations of conventional MRI and allow for improved characterization of brain tissue microstructure (Deoni 2010; Does 2018).

For the HBCD study, the MRI WG adopted the three-dimensional quantification using an interleaved Look–Locker acquisition sequence with a T2 preparation pulse (3D-QALAS) (Kvernby et al. 2014), which is a time-efficient 3D method capable of simultaneous estimation of T1, T2 and PD maps from a single scan and is available and tested across all three major MRI vendors (Fujita et al. 2019).

### Quality Control & Known Issues
QC was performed via visual inspection of the parametric maps, region of interest analysis, and comparison of quantitative parametric values.

Subject matter experts note that currently, the SyMRI toolbox does not incorporate externally acquired B1+ field maps into the quantitative T1, T2, and PD estimation. In addition, there are variations of the estimated quantitative T1 values across the three MRI vendors and across age. Current estimates do not align well with prior literature and may result from certain assumptions in the modeling procedures. This is currently a work in progress to correct. As a result, the quantitative T1 (and consequently the PD) values will not be initially released. 

<details class="collapsible references">
  <summary class="references" style="font-size: 1.2em; margin: 0 0 5x;">References</summary>
 <ul>
<li><p>Dean III, D. C., Tisdall, M. D., Wisnowski, J. L., Feczko, E., Gagoski, B., Alexander, A. L., ... &amp; HBCD MRI Working Group. (2024). Quantifying brain development in the HEALthy Brain and Child Development (HBCD) Study: The magnetic resonance imaging and spectroscopy protocol. <em>Developmental Cognitive Neuroscience</em>, 70, 101452. <a href="https://doi.org/10.1016/j.dcn.2024.101452">https://doi.org/10.1016/j.dcn.2024.101452</a></p></li>
<li>Deoni, S. C. L. (2010). Quantitative relaxometry of the brain. <i>Topics in Magnetic Resonance Imaging: TMRI</i>, 21(2), 101–113. <a href="https://doi.org/10.1097/RMR.0b013e31821e56d8">https://doi.org/10.1097/RMR.0b013e31821e56d8</a></p></li>
<li>Does, M. D. (2018). Inferring brain tissue composition and microstructure via MR relaxometry. <i>NeuroImage</i>, 182, 136–148. <a href="https://doi.org/10.1016/j.neuroimage.2017.12.087">https://doi.org/10.1016/j.neuroimage.2017.12.087</a></p></li>
<li>Fujita, S., Hagiwara, A., Hori, M., Warntjes, M., Kamagata, K., Fukunaga, I., Andica, C., Maekawa, T., Irie, R., Takemura, M. Y., Kumamaru, K. K., Wada, A., Suzuki, M., Ozaki, Y., Abe, O., &amp; Aoki, S. (2019). Three-dimensional high-resolution simultaneous quantitative mapping of the whole brain with 3D-QALAS: An accuracy and repeatability study. <i>Magnetic Resonance Imaging</i>, 63, 235–243. <a href="https://doi.org/10.1016/j.mri.2019.08.031">https://doi.org/10.1016/j.mri.2019.08.031</a></p></li>
<li>Kvernby, S., Warntjes, M. J. B., Haraldsson, H., Carlhäll, C.-J., Engvall, J., & Ebbers, T. (2014). Simultaneous three-dimensional myocardial T1 and T2 mapping in one breath hold with 3D-QALAS. <i>Journal of Cardiovascular Magnetic Resonance: Official Journal of the Society for Cardiovascular Magnetic Resonance</i>, 16(1), 102. <a href="https://doi.org/10.1186/s12968-014-0102-0" target="_blank">https://doi.org/10.1186/s12968-014-0102-0</a></li>
</ul>
</details>

## Sy-T1w, Sy-T2w
**Full Name**: Synthetically generated T1- and T2-weighted volumes      
**Acronym/Brief Names**: Sy-T1w, Sy-T2w     
**Construct**: Processing

The 3D-QALAS technique in conjunction with the Synthetic MRI (SyMRI) toolbox provides synthetically generated T1-weighted and T2-weighted volumes. Synthetic images are generated by substituting quantitative estimates of T1 and T2 relaxation times back into the governing MR signal equation (or the Bloch equations) for each sequence. This provides flexibility in being able to produce images of various contrasts without needing to acquire these data at a given set of imaging parameters. 

<details class="collapsible references">
  <summary class="references" style="font-size: 1.2em; margin: 0 0 5x;">References</summary>
<ul>
<li>Deoni, S. C. L., Rutt, B. K., & Peters, T. M. (2006). Synthetic T1-weighted brain image generation with incorporated coil intensity correction using DESPOT1. <i>Magnetic Resonance Imaging</i>, 24(9), 1241–1248. <a href="https://doi.org/10.1016/j.mri.2006.03.015">https://doi.org/10.1016/j.mri.2006.03.015</a></li>
<li>Gonçalves, F. G., Serai, S. D., & Zuccoli, G. (2018). Synthetic brain MRI. <i>Topics in Magnetic Resonance Imaging: TMRI</i>, 27(6), 387–393. <a href="https://doi.org/10.1097/rmr.0000000000000189">https://doi.org/10.1097/rmr.0000000000000189</a></li>
<li>Ji, S., Yang, D., Lee, J., Choi, S. H., Kim, H., & Kang, K. M. (2022). Synthetic MRI: Technologies and applications in neuroradiology. <i>Journal of Magnetic Resonance Imaging</i>, 55(4), 1013–1025. <a href="https://doi.org/10.1002/jmri.27440">https://doi.org/10.1002/jmri.27440</a></li>
</ul>
</details>


 


 



