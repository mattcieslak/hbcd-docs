# Visual Evoked Potential Task
*See [Common Measure Details](measures_all.md) for information on implementation, data collection, quality control & known issues, and additional information.*

**Full Name**: Visual Evoked Potential Task  
**Acronym/Brief Name**: VEP  

**Description**     
The Visual Evoked Potential Task (VEP) (v.11.29.23) measures cortical responses to flashing checkerboard visual stimuli, shown for the duration of the task: 
>>>>>![VEP checkerboard image](images/eeg-vep-checkerboard.png)

VEP amplitude and latency decreases with age during the first three years of life. The VEP has been associated with concurrent and later developmental outcomes as a function of prenatal substance exposures (Margolis et al., 2024), early visual enrichment or deprivation (Jensen et al., 2019), vision system maturation (Lippé et al., 2009), neurodevelopmental disorders (e.g., ASD and ADHD; Cremone- Caira et al., 2023; Nazhvani et al., 2013), and reading and learning disabilities (Shandiz et al., 2017). The morphology of the VEP likely reflects varying degrees of synaptic efficiency and as such, can be used as a readout of general cortical function. The task elicits a VEP response in the occipital area (Oz), consisting of the, N1 (first negative peak), P1 (first positive peak), and N2 (second negative peak) components. See Fox et al. (2024) for more information about the VEP task.  

**Summary**     
The Visual Evoked Potential Task (v.11.29.23) measures development of visual cortex and response to stimuli, reflecting underlying cortical development. The measure includes rigorous QC procedures to ensure data integrity and reliability.





<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Collapsible Section</title>
  <style>
    .collapsible {
      background-color: #f1f1f1;
      color: #333;
      cursor: pointer;
      padding: 10px;
      width: 100%;
      border: none;
      text-align: left;
      outline: none;
      font-size: 16px;
    }

    .active, .collapsible:hover {
      background-color: #ddd;
    }

    .content {
      padding: 0 15px;
      display: none;
      overflow: hidden;
      background-color: #f9f9f9;
    }
  </style>
</head>
<body>

<button type="button" class="collapsible"><b>REFERENCES <i>(click to expand)</i></b></button>
<div class="content">
  <ul>
    <li>Cremone-Caira, A., Braverman, Y., MacNaughton, G. A., Nikolaeva, J. I., & Faja, S. (2023). Reduced Visual Evoked Potential Amplitude in Autistic Children with Co-Occurring Features of Attention-Deficit/Hyperactivity Disorder. <em>Journal of Autism and Developmental Disorders</em>. <a href="https://doi.org/10.1007/s10803-023-06005-7" target="_blank">https://doi.org/10.1007/s10803-023-06005-7</a></li>
    <li>Fox, N.A., Pérez-Edgar, K., Morales, S., Brito, N. H., Campbell, A. M., Cavanagh, J. F., Gabard-Durnam, L. J., Hudac, C. M., Key, A. P., Larson-Prior, L. J., Pedapati, E. V., Norton, E. S., Reetzke, R., Roberts, T. P., Rutter, T. M., Scott, L. S., Shuffrey, L. C., Antúnez, M., Boylan, M. R., … Yoder, L. (2024). The development and structure of the Healthy Brain and Child Development (HBCD) study EEG Protocol. <em>Developmental Cognitive Neuroscience</em>, 69, 101447. <a href="https://doi.org/10.1016/j.dcn.2024.101447" target="_blank">https://doi.org/10.1016/j.dcn.2024.101447</a></li>
    <li>Jensen, S. K. G., Kumar, S., Xie, W., Tofail, F., Haque, R., Petri, W. A., & Nelson, C. A. (2019). Neural correlates of early adversity among Bangladeshi infants. <em>Scientific Reports</em>, 9(1), 3507. <a href="https://doi.org/10.1038/s41598-019-39242-x" target="_blank">https://doi.org/10.1038/s41598-019-39242-x</a></li>
    <li>Lippé, S., Kovacevic, N., & McIntosh, A. R. (2009). Differential Maturation of Brain Signal Complexity in the Human Auditory and Visual System. <em>Frontiers in Human Neuroscience</em>, 3, 48. <a href="https://doi.org/10.3389/neuro.09.048.2009" target="_blank">https://doi.org/10.3389/neuro.09.048.2009</a></li>
    <li>Margolis, E. T., Davel, L., Bourke, N. J., Bosco, C., Zieff, M. R., Monachino, A. D., Mazubane, T., Williams, S. R., Miles, M., & Jacobs, C. A. (2024). Longitudinal effects of prenatal alcohol exposure on visual neurodevelopment over infancy. <em>Developmental Psychology</em>. <a href="https://psycnet.apa.org/record/2024-66755-001" target="_blank">https://psycnet.apa.org/record/2024-66755-001</a></li>
    <li>Nazhvani, A. D., Boostani, R., Afrasiabi, S., & Sadatnezhad, K. (2013). Classification of ADHD and BMD patients using visual evoked potential. <em>Clinical Neurology and Neurosurgery</em>, 115(11), 2329–2335. <a href="https://doi.org/10.1016/j.clineuro.2013.08.009" target="_blank">https://doi.org/10.1016/j.clineuro.2013.08.009</a></li>
    <li>Shandiz, J. H., Heyrani, M., Sobhani-Rad, D., Salehinejad, Z., Shojaei, S., Khoshsima, M. J., Azimi, A., Yekta, A. A., & Yazdi, S. H. H. (2017). Pattern Visual Evoked Potentials in Dyslexic Children. <em>Journal of Ophthalmic & Vision Research</em>, 12(4), 402–406. <a href="https://doi.org/10.4103/jovr.jovr_106_16" target="_blank">https://doi.org/10.4103/jovr.jovr_106_16</a></li>
  </ul>
</div>

<script>
  const coll = document.querySelector('.collapsible');
  coll.addEventListener('click', function() {
    this.classList.toggle('active');
    const content = this.nextElementSibling;
    content.style.display = content.style.display === 'block' ? 'none' : 'block';
  });
</script>

</body>
</html>
<br>