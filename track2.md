---
layout: distill
title: LAScarQS++
description: Left Atrial and Scar Quantification & Segmentation
permalink: /track2/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Task
  - name: Data
  - name: Metrics & Award
  - name: Rules
  - name: Registration
  - name: Submission Guidance
  - name: Timeline
  - name: Citations
  - name: Contact
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
Atrial fibrillation (AF), the most prevalent cardiac arrhythmia, is poised to escalate in frequency due to aging populations <d-cite key="lascarqs1"></d-cite>.
Radiofrequency catheter ablation, a common AF therapy, faces challenges due to high recurrence rates <d-cite key="lascarqs2"></d-cite>.
Cardiac digital twin provides personalized *in-silico* cardiac representations to infer multi-scale properties associated with cardiac mechanisms <d-cite key="lascarqs3"></d-cite><d-cite key="lascarqs4"> </d-cite>. 
It has shown great promise in personalized targeted ablation of persistent AF <d-cite key="lascarqs5"></d-cite> (see Fig. 1).
To create a digital twin, it is important to reconstruct the left atrial (LA) geometry with the location of scars from LGE MRI <d-cite key="lascarqs6"></d-cite>.
However, automatic quantification and analysis of LA scars can be quite challenging due to the low image quality, thin wall, the surrounding enhanced regions, and the complex patterns of scars <d-cite key="lascarqs7"></d-cite>.
Deep learning (DL) methods have shown promise in LGE MRI analysis, yet their performance often falters in new domains due to domain shifts <d-cite key="lascarqs8"></d-cite><d-cite key="lascarqs9"></d-cite>.
The LAScarQS++ track aims to address these issues, driving the advancement of DL models that precisely delineate LA cavity and scars and ultimately revolutionize personalized AF treatment.

## Task

{% include figure.liquid loading="eager" path="/assets/img/lascarqs2.png" class="img-fluid" zoomable=true caption="Figure 2." %}
The target of this track is to automatically segment LA cavity and quantify LA scars from LGE MRI (see Fig. 2). The track will provide 200+ LGE MRIs globally, i.e., from multiple imaging centers around the world, for developing novel algorithms that can quantify or segment LA cavity and scars. The track presents an open and fair platform for various research groups to test and validate their methods on these datasets acquired from the clinical environment. To ensure data privacy, the platform will enable remote training and testing on the dataset from different centers in local and the dataset can keep invisible.

The selected papers will be published in our proceedings (see [previous proceedings](https://www.google.co.uk/books/edition/Left_Atrial_and_Scar_Quantification_and/dkq9EAAAQBAJ?hl=en&gbpv=0)).

Topics may cover (not exclusively):
- Cardiac digital twins
- Atrial fibrillation
- Cardiac image segmentation
- Model generalization
- Joint optimization
- Multi-task learning
- Personalized healthcare

## Data

### Data acquisition information
We include 200+ multi-center LGE MRIs (enhanced.nii.gz) from different countries, with manual segmentation of LA cavity (atriumSegImgMO.nii.gz) and/ or scarring region (scarSegImgM.nii.gz).
All these clinical data have got institutional ethic approval and have been anonymized (please follow the data usage agreement, i.e., CC BY NC ND).
The details of these LGE MRI are listed below:

*Center A*: 154 LGE MRIs

This data was original collected from Utah [NAMIC-CARMA](https://www.insight-journal.org/midas/collection/view/197) with permission for release. [2018 Atrial Segmentation Challenge](https://atriaseg2018.cardiacatlas.org/) refined the LA segmentation of Utah NAMIC-CARMA dataset before final release.  Therefore, we adopted the refine dataset, and further fixed the resolution irregularities existing in this dataset. The clinical images were acquired with Siemens Avanto 1.5T or Vario 3T using free-breathing (FB) with navigator-gating.  The spatial resolution of the 3D LGE MRI scan was 0.625 × 0.625 × 2.5 mm.  The patient underwent an MR examination prior to ablation or was 3-6 months after ablation.

*Center B*: 20 LGE MRIs

This data was original collected from Beth Israel Deaconess Medical Center and was used in [ISBI2012 Left Atrium Fibrosis and Scar Segmentation Challenge](https://www.cardiacatlas.org/challenges/left-atrium-fibrosis-and-scar-segmentation-challenge/). We selected part of the dataset from this challenge and refine their manual segmentation before release. The clinical images were acquired with Philips Acheiva 1.5T using FB and navigator-gating with fat suppression. The spatial resolution of one 3D LGE MRI scan was 1.4 × 1.4 × 1.4 mm. The patient underwent an MR examination prior to ablation or was 1 month after ablation.

*Center C*: 20 LGE MRIs

This data was original collected from King’s College London and was used in [ISBI2012 Left Atrium Fibrosis and Scar Segmentation Challenge](https://www.cardiacatlas.org/challenges/left-atrium-fibrosis-and-scar-segmentation-challenge/). We selected part of the dataset from this challenge and refine their manual segmentation before release. The clinical images were also acquired with Philips Acheiva 1.5T using FB and navigator-gating with fat suppression. The spatial resolution of one 3D LGE MRI scan was 1.3 × 1.3 × 4.0 mm. The patient underwent an MR examination prior to ablation or was 3-6 months after ablation.

<!--
*Center C-2*: 40 LGE MRIs

This data was collected from King’s College London/ St Thomas' Hospital with permission for release. All patients underwent CMR imaging on a 1.5T scanner (Magnetom Area, Siemens Healthineers, Erlangen, Germany) using a previously described protocol. Twenty minutes after contrast administration, late gadolinium enhancement imaging was performed using an ECG-triggered, respiratory navigated, 3D whole heart, inversion recovery spoiled gradient echo sequence in axial orientation (spatial resolution 1.3 mm × 1.3 mm × 4.0 mm reconstructed to 1.3 × 1.3 × 2 mm, TR 4 ms, TE 2 ms, flip angle 20°), phase encoding direction; anterior–posterior, frequency encoding direction; right–left, parallel imaging; GRAPPA factor 2.
-->



### Data split

The dataset has been divided into three main parts: training, validation, and test sets:

*Task 1*:
- **Training Set**: 60 LGE MRIs from Center A
- **Validation Set**: 10 LGE MRIs from Center A
- **Test Set**: 24 LGE MRIs from Center A
  
*Task 2*:
- **Training Set**: 130 LGE MRIs from Centers A
- **Validation Set**: 10 LGE MRIs from Center A and 10 LGE MRIs from Center C
- **Test Set**: 14 LGE MRIs from Center A, 20 LGE MRIs from Center B, and 10 LGE MRIs from Center C  <!-- , 40 LGE MRIs from Center 2.2-->

### Data Format
Each LGE MRI and gold standard label(s) of patients will be provided in the NIfTI format as follows:
- enhanced.nii.gz (LGE MRI)
- atriumSegImgMO.nii.gz (gold standard LA cavity label)
- scarSegImgM.nii.gz (gold standard LA scar label, for task 1 only)

The submitted format of the prediction for the participants could be named as follows:
- LA_predict.nii.gz (predicted LA cavity label)
- scar_predict.nii.gz (predicted LA scar label)
  
## Metrics & Award
### Metrics
The performance of LA cavity segmentation or LA scar quantification results will be evaluated by：

*Task 1*:
- *Generalized Dice Similarity Coefficient (G-DSC)* <d-cite key="lascarqs6">
- *Accuracy (ACC)*
- *Sensitivity (SEN)*

*Task 2*:
- *Dice Similarity Coefficient (DSC)*
- *Average Surface Distance (ASD)*
- *Hausdorff Distance (HD)*

### Award

Tasks 1 and 2 will be evaluated and ranked seperately, based on the performance of the model, the novelty of the method, the quality of the submitted paper, and the performance of the presentation (either oral presentation or poster), etc. The best work will be selected with awards, similar to [LAScarQS 2022](https://zmiclab.github.io/projects/lascarqs22/). Specifically, we will prepare one **Champion Winner Award** and one **Best Paper Award**.

## Rules
1. External data sets and pre-trained models are NOT allowed in this track.
2. Only automatic methods are permitted.
3. Participants are encouraged to attempt both tasks, but they also can choose to focus on either task 1 or task 2. 
   
## Registration
To access the dataset, please register in the [LAScarQS++ registration platform](http://zmic.org.cn/care_2024/eval/register?track=LAScarQS%2B%2B).

## Submission Guidance

### Model Submission
After registration, we will assign the participant an account to login into our [LAScarQS++ evaluation platform](http://zmic.org.cn/care_2024/eval/login?track=LAScarQS%2B%2B). Participants can directly upload your predictions on the validation data (in nifty format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/test_submission) for testing.
### Paper Submission
Please refer to our [paper submission guidance](/care_2024/paper_submission).

## Timeline
The schedule for this track is as follows. All deadlines(DDLs) are on 23:59 in Pacific Standard Time.

<table class="table table-sm table-hover border-bottom">
    <tr>
    <td class="text-left"><strong>Training Data Release</strong></td>
    <th scope="row" style="width: 60%" class="text-right">May 10, 2024</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Validation Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>June 10, 2024 to July 7, 2024 (DDL)</s> July 1, 2024 to July 30, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Test Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>July 7, 2024 to August 7, 2024 (DDL)</s> TBC</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Abstract Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>July 15, 2024 (DDL)</s> July 25, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Paper Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right">August 15, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Notification</strong></td>
    <th scope="row" style="width: 60%" class="text-right">September 15, 2024</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Camera Ready</strong></td>
    <th scope="row" style="width: 60%" class="text-right">September 25, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Workshop (Half-Day)</strong></td>
    <th scope="row" style="width: 60%" class="text-right">October 10, 2024</th>
    </tr>
</table>

## Citations
Please cite these papers when you use the data for publications:
```bib
 @article{journal/MedIA/li2022,
  title={Medical image analysis on left atrial LGE MRI for atrial fibrillation studies: A review},
  author={Li, Lei and Zimmer, Veronika A and Schnabel, Julia A and Zhuang, Xiahai},
  journal={Medical image analysis},
  volume={77},
  pages={102360},
  year={2022},
  publisher={Elsevier}
}

@article{journal/MedIA/li2020,
  title={Atrial scar quantification via multi-scale CNN in the graph-cuts framework},
  author={Li, Lei and Wu, Fuping and Yang, Guang and Xu, Lingchao and Wong, Tom and Mohiaddin, Raad and Firmin, David and Keegan, Jennifer and Zhuang, Xiahai},
  journal={Medical image analysis},
  volume={60},
  pages={101595},
  year={2020},
  publisher={Elsevier}
}

@article{journal/MedIA/li2022,
  title={AtrialJSQnet: a new framework for joint segmentation and quantification of left atrium and scars incorporating spatial and shape information},
  author={Li, Lei and Zimmer, Veronika A and Schnabel, Julia A and Zhuang, Xiahai},
  journal={Medical image analysis},
  volume={76},
  pages={102303},
  year={2022},
  publisher={Elsevier}
}

@inproceedings{conf/MICCAI/li2021,
  title={AtrialGeneral: domain generalization for left atrial segmentation of multi-center LGE MRIs},
  author={Li, Lei and Zimmer, Veronika A and Schnabel, Julia A and Zhuang, Xiahai},
  booktitle={Medical Image Computing and Computer Assisted Intervention--MICCAI 2021: 24th International Conference, Strasbourg, France, September 27--October 1, 2021, Proceedings, Part VI 24},
  pages={557--566},
  year={2021},
  organization={Springer}
}
```

## Contact

If you have any questions regarding the LAScarQS++ track, please feel free to contact:

- Dr Lei Li: [lilei.sky@outlook.com](mailto:lilei.sky@outlook.com)
- Xingtao Lin: [231110040@fzu.edu.cn](mailto:231110040@fzu.edu.cn)

<!-- ## Organizer and Committee Team

- Dr Lei Li: University of Southampton, UK
- Dr Yingliang Ma: University of East Anglia, UK
- Dr Guang Yang: Imperial College London, UK -->
