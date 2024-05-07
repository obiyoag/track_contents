---
layout: distill
title: LAScarQS++
description: Left Atrial and Scar Quantification & Segmentation
permalink: /track2/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Overview of the Track
  - name: Dataset
  - name: Submission Guidance
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
The target of this track is to automatically segment LA cavity and quantify LA scars from LGE MRI (see Fig. 2). The track will provide 234 LGE MRIs globally, i.e., from multiple imaging centers around the world, for developing novel algorithms that can quantify or segment LA cavity and scars. The track presents an open and fair platform for various research groups to test and validate their methods on these datasets acquired from the clinical environment. To ensure data privacy, the platform will enable remote training and testing on the dataset from different centers in local and the dataset can keep invisible.

The best work will be selected with awards, similar to LAScarQS 2022. A work is assessed based on the novelty of the methodologies, quality of the manuscript, presentation of their paper as well as the test results.

The selected papers will be published in our proceedings (see previous proceedings).

Topics may cover (not exclusively):
- Cardiac digital twins
- Atrial fibrillation
- Cardiac image segmentation
- Model generalization
- Joint optimization
- Multi-task learning
- Personalized healthcare

## Dataset

### Data acquisition information
We include 234 multi-center LGE MRIs (enhanced.nii.gz) from different countries, with manual segmentation of LA cavity (atriumSegImgMO.nii.gz) and/ or scarring region (scarSegImgM.nii.gz).
All these clinical data have got institutional ethic approval and have been anonymized (please follow the data usage agreement, i.e., CC BY NC ND).
The details of these LGE MRI are listed below:

- **Center 1** 20 LGE MRIs

This data was original collected from Beth Israel Deaconess Medical Center and was used in [ISBI2012 Left Atrium Fibrosis and Scar Segmentation Challenge](https://www.cardiacatlas.org/challenges/left-atrium-fibrosis-and-scar-segmentation-challenge/). We selected part of the dataset from this challenge and refine their manual segmentation before release. The clinical images were acquired with Philips Acheiva 1.5T using FB and navigator-gating with fat suppression. The spatial resolution of one 3D LGE MRI scan was 1.4 × 1.4 × 1.4 mm. The patient underwent an MR examination prior to ablation or was 1 month after ablation.

- **Center 2.1** 20 LGE MRIs

This data was original collected from King’s College London and was used in [ISBI2012 Left Atrium Fibrosis and Scar Segmentation Challenge](https://www.cardiacatlas.org/challenges/left-atrium-fibrosis-and-scar-segmentation-challenge/). We selected part of the dataset from this challenge and refine their manual segmentation before release. The clinical images were also acquired with Philips Acheiva 1.5T using FB and navigator-gating with fat suppression. The spatial resolution of one 3D LGE MRI scan was 1.3 × 1.3 × 4.0 mm. The patient underwent an MR examination prior to ablation or was 3-6 months after ablation.

- **Center 2.2** 40 LGE MRIs

This data was collected from King’s College London/ St Thomas' Hospital with permission for release. All patients underwent CMR imaging on a 1.5T scanner (Magnetom Area, Siemens Healthineers, Erlangen, Germany) using a previously described protocol. Twenty minutes after contrast administration, late gadolinium enhancement imaging was performed using an ECG-triggered, respiratory navigated, 3D whole heart, inversion recovery spoiled gradient echo sequence in axial orientation (spatial resolution 1.3 mm × 1.3 mm × 4.0 mm reconstructed to 1.3 × 1.3 × 2 mm, TR 4 ms, TE 2 ms, flip angle 20°), phase encoding direction; anterior–posterior, frequency encoding direction; right–left, parallel imaging; GRAPPA factor 2.

- **Center 3** 154 LGE MRIs

This data was original collected from Utah [NAMIC-CARMA](https://www.insight-journal.org/midas/collection/view/197) with permission for release. 2018 Atrial Segmentation Challenge[(https://atriaseg2018.cardiacatlas.org/)] refined the LA segmentation of Utah NAMIC-CARMA dataset before final release.  Therefore, we adopted the refine dataset, and further fixed the resolution irregularities existing in this dataset. The clinical images were acquired with Siemens Avanto 1.5T or Vario 3T using free-breathing (FB) with navigator-gating.  The spatial resolution of the 3D LGE MRI scan was 0.625 × 0.625 × 2.5 mm.  The patient underwent an MR examination prior to ablation or was 3-6 months after ablation.

### Data split

The dataset has been divided into three main parts: training, validation, and test sets:

*Task 1*:
- **Training Set**: 60 LGE MRIs from Center 3
- **Validation Set**: 10 LGE MRIs from Center 3
- **Test Set**: 24 LGE MRIs from Center 3
  
*Task 2*:
- **Training Set**: 130 LGE MRIs from Centers 3
- **Validation Set**: 10 LGE MRIs from Center 2.1 and 10 LGE MRIs from Center 3
- **Test Set**: 20 LGE MRIs from Center 1, 10 LGE MRIs from Center 2.1, 40 LGE MRIs from Center 2.2, and 14 LGE MRIs from Center 3

### Data access
To access the dataset, please register in the [LAScarQS++ registration platform](http://zmic.org.cn/care_2024/eval/register?track=LAScarQS%2B%2B).

## Submission Guidance

### Model submission
After you register in this challenge, we will assign you of a account to login in our [LAScarQS++ evaluation platform](http://zmic.org.cn/care_2024/eval/login?track=LAScarQS%2B%2B).
You can directly upload your predictions on the validation data (in nifty format) via the website. Note that evaluation on validation data will be allowed up to 10 times for each task per team.

<!-- For evaluation, we will employ Dice score, Accuracy,... -->

### Paper submission
tbc

### Contact

If you have any questions regarding the LAScarQS track, please feel free to contact:

- Dr Lei Li: [lilei.sky@outlook.com](mailto:lilei.sky@outlook.com)

<!-- ## Organizer and Committee Team

- Dr Lei Li: University of Southampton, UK
- Dr Yingliang Ma: University of East Anglia, UK
- Dr Guang Yang: Imperial College London, UK -->
