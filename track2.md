---
layout: distill
title: LAScarQS++
description: Left Atrial and Scar Quantification & Segmentation
permalink: /track2/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Overview of the Track
_styles: >
  d-article {
    contain: layout style;
    overflow-x: hidden;
    border-top: 1px solid rgba(0, 0, 0, 0.1);
    padding-top: 2rem;
    color: rgba(0, 0, 0, 0.8);
  }

  d-article > * {
    grid-column: text;
  }
---

## Motivation

{% include figure.liquid loading="eager" path="/assets/img/lascarqs1.png" class="img-fluid" zoomable=true caption="Figure 1." %}
Atrial fibrillation (AF), the most prevalent cardiac arrhythmia, is poised to escalate in frequency due to aging populations<d-cite key="lascarqs1"></d-cite>.
Radiofrequency catheter ablation, a common AF therapy, faces challenges due to high recurrence rates <d-cite key="lascarqs2"></d-cite>.
Cardiac digital twin provides personalized *in-silico* cardiac representations to infer multi-scale properties associated with cardiac mechanisms<d-cite key="lascarqs3"></d-cite><d-cite key="lascarqs4"></d-cite>. 
It has shown great promise in personalized targeted ablation of persistent AF<d-cite key="lascarqs5"></d-cite> (see Fig. 1).
To create a digital twin, it is important to reconstruct the left atrial (LA) geometry with the location of scars from LGE MRI<d-cite key="lascarqs6"></d-cite>.
However, automatic quantification and analysis of LA scars can be quite challenging due to the low image quality, thin wall, the surrounding enhanced regions, and the complex patterns of scars<d-cite key="lascarqs7"></d-cite>.
Deep learning (DL) methods have shown promise in LGE MRI analysis, yet their performance often falters in new domains due to domain shifts<d-cite key="lascarqs8"></d-cite><d-cite key="lascarqs9"></d-cite>.
The LAScarQS++ track aims to address these issues, driving the advancement of DL models that precisely delineate LA cavity and scars and ultimately revolutionize personalized AF treatment.



## Overview of the Track

{% include figure.liquid loading="eager" path="/assets/img/lascarqs2.png" class="img-fluid" zoomable=true caption="Figure 2." %}
The target of this track is to automatically segment LA cavity and quantify LA scars from LGE MRI (see Fig. 2). The track will provide 224 LGE MRIs globally, i.e., from multiple imaging centers around the world, for developing novel algorithms that can quantify or segment LA cavity and scars. The track presents an open and fair platform for various research groups to test and validate their methods on these datasets acquired from the clinical environment. To ensure data privacy, the platform will enable remote training and testing on the dataset from different centers in local and the dataset can keep invisible.

The best work will be selected with awards, similar to LAScarQS 2022. A work is assessed based on the novelty of the methodologies, quality of the manuscript, presentation of their paper as well as the test results. 

The selected papers will be published in our proceedings (see previous proceedings).

Topics may cover (not exclusively):
- Cardiac digital twins
- Atrial fibrillation
- Cardiac image segmentation 
- Model generalization
- Joint optimization
