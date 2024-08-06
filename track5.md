---
layout: distill
title: WHS++
description: Whole Heart Segmentation
permalink: /track5/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Task
  - name: Data
  - name: Guidance for Training Strategies
  - name: Metrics & Ranking
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
Cardiovascular diseases (CVDs), as the leading cause of death globally<d-cite key="whs1"></d-cite>, necessitate precise morphological and pathological quantification through segmentation of crucial cardiac structures from medical images<d-cite key="whs2"></d-cite>. However, whole heart segmentation (WHS) faces challenges including heart shape variability during the cardiac cycle, clinical artifacts like motion and poor contrast-to-noise ratio, as well as domain shifts in multi-center data and the distinct modalities of CT and MRI. The WHS++ track serves to inspire innovative solutions in the realms of biomedical imaging and computer vision, striving to overcome these challenges and advance automated WHS for enhanced understanding and treatment of CVDs.

## Task
{% include figure.liquid loading="eager" path="/assets/img/whs.png" class="img-fluid" zoomable=true caption="Figure 1. Overview of the WHS++ track" %}

The dataset includes **104 CT** and **102 MRI** volumes, sourced globally from **6** imaging centers. The objective of this track is to achieve precise segmentation of seven substructures of the whole heart, with robustness against domain shifts (see Fig. 1).  The specific  substructures, each associated with a unique label value, are:

1. **Left Ventricular Blood Cavity (LV)** - Label value: 500
2. **Right Ventricular Blood Cavity (RV)** - Label value: 600
3. **Left Atrial Blood Cavity (LA)** - Label value: 420
4. **Right Atrial Blood Cavity (RA)** - Label value: 550
5. **Myocardium of the Left Ventricle (Myo)** - Label value: 205
6. **Ascending Aorta (AO)** - Label value: 820; defined as the aortic trunk from the aortic valve to the superior level of the atria.
7. **Pulmonary Artery (PA)** - Label value: 850; defined as the initial segment from the pulmonary valve to the bifurcation point.

**Note on Great Vessels:** The great vessels of interest, comprising the ascending aorta and pulmonary artery, are specifically defined due to variations in the fields of view across different scans. This uniform definition is crucial for ensuring consistency across evaluations. During the assessment, segmentation results for these vessels will be truncated to average lengths measured in healthy subjects, although participants are encouraged to extend their segmentation beyond these lengths. Our provided manual segmentations similarly cover more than the defined trunk measurements.

The selected papers will be published as part of the MICCAI Satellite Events joint LNCS proceedings.([see previous proceedings](https://link.springer.com/book/10.1007/978-3-319-75541-0)).

Topics may cover (not exclusively):

- Cardiac anatomy segmentation
- Cardiac image registration
- Cardiac modeling
- Domain adaptation
- Model generalization

## Data

### Data overview

We include **206** multi-modality whole heart images from **6** centers in different countries, including **104** cardiac CT/CTA and **102** cardiac MRI in 3D that cover the whole heart substructures. 

The data were collected based on in vivo clinical environment and the data were used in clinics, covering a wide range of cardiac diseases. So the data had various image quality, some were with relative poor quality. However, it is necessary to include these datasets to validate the robustness of the developed algorithms when it comes to real clinical usage.

### Data Split

The dataset is divided into training, validation, and test sets:

- **Training Set**: 40 CT and 46 MR images
- **Validation Set**: 30 CT and 20 MR images
- **Test Set**: 34 CT and 36 MR images

Further details are provided in Fig. 2. Note that both the images and labels of the test set will not be released.

{% include figure.liquid loading="eager" path="/assets/img/whs2.png" class="img-fluid" zoomable=true caption="Figure 2." %}

### Data Format

All data will be provided in the NIfTI format as [Case Identifier]_[image/label].nii.gz. 

### Data Acquisition

The cardiac CT/CTA data were acquired using standard coronary CT angiography protocols. At Center A, imaging was conducted with 64-slice Philips CT scanners. Center B used a dual-source SIEMENS CT scanner or a high-end, single-source GE CT scanner. The cardiac MRI data were obtained using various steady-state free precession (SSFP) sequences, adaptable for both free-breathing and breath-held imaging. Centers C and D employed either a 1.5T Philips scanner or a Siemens Avanto 1.5T scanner for scanning. Center E utilized Philips Achieva 1.5T scanners. Center F conducted its imaging with a Siemens Avanto 1.5T scanner. This diversity in the data acquisition process across centers underscores the extensive scope and scale of the dataset.

### Guidance for Training Strategies

To facilitate a well-informed training process, information about the imaging centers will be provided alongside the cases, indicated by the case naming (refer to Fig. 2).  Participants are strongly encouraged to use this information to design training strategies that aim for high generalization capability. This approach is intended to promote the development of algorithms that perform robustly not only under controlled conditions but also across diverse real-world clinical environments.

## Metrics & Ranking

### Metrics

The performance of segmentation results will be assessed through: 

- Dice Similarity Coefficient (DSC), 
- Hausdorff Distance (HD), and 
- Average Surface Distance (ASD). 

### Aim

Accuracy and robustness are crucial for the success of automatic WHS algorithms in clinical settings. Therefore, the final evaluation during the test phase will include images from both centers that have been involved in previous phases and a new, unseen center (detailed in the Data Information section). 

### Rank

Outstanding contributions will be recognized with awards, similar to [MM-WHS 2017](https://zmiclab.github.io/zxh/0/mmwhs/)<d-cite key="whs3"></d-cite> . Submissions will be evaluated based on
- the test results,
- the novelty of their methodologies, 
- the quality of their manuscript, and
- the clarity of their presentation.

For test results, both in-sample performance from seen centers and generalization capabilities at the unseen center will be considered. The empirical results will be ranked by averaging the performance scores from both scenarios.


## Rules

- **Only automatic methods are acceptable.** Participants must utilize algorithms that do not require manual intervention or human-assisted processes for the segmentation task.
- **External data sets and pre-trained models are not allowed in this track.** The solutions must be developed using only the data provided within the scope of this track and cannot leverage any external datasets or models for assistance.

## Registration

Please register [here](http://zmic.org.cn/care_2024/eval/register?track=WHS%2B%2B) to participate in the challenge and get access to the dataset!!


## Submission Guidance

### Model Submission
After registration, we will assign participants an account to login into our [WHS++ evaluation platform](http://zmic.org.cn/care_2024/eval/login?track=WHS%2B%2B). Participants can directly upload your predictions on the validation data (in nifty format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/test_submission) for testing.
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
**Please cite these papers when you use the data for publications:**

```
@article{Zhuang2016MSMMA,
  Author = {Zhuang, Xiahai and Shen, Juan},
  Title = {Multi-scale patch and multi-modality atlases for whole heart
     segmentation of MRI},
  Journal = {Medical Image Analysis},
  Year = {2016},
  Volume = {31},
  Pages = {77-87},
}

@article{Zhuang2019evaluation,
  Author={Zhuang, Xiahai and Li, Lei and Payer, Christian and Stern, Darko and Urschler, Martin and Heinrich, Mattias P and Oster, Julien and Wang, Chunliang and Smedby, {\"O}rjan and Bian, Cheng and others},
  Title={Evaluation of algorithms for multi-modality whole heart segmentation: an open-access grand challenge},
  Journal={Medical image analysis},
  Year={2019},
  Volume={58},
  Pages={101537}，
}

@article{Zhuang2019MvMM,
  Author = {Zhuang, Xiahai},
  Title = {Multivariate Mixture Model for Myocardial Segmentation Combining
     Multi-Source Images},
  Journal = {IEEE Transactions on Pattern Analysis and Machine Intelligence},
  Year = {2019},
  Volume = {41},
  Number = {12},
  Pages = {2933-2946},
}

@article{GAO2023BayeSeg,
  Author = {Gao, Shangqi and Zhou, Hangqi and Gao, Yibo and Zhuang, Xiahai},
  Title = {BayeSeg: Bayesian modeling for medical image segmentation with
     interpretable generalizability},
  Journal = {Medical Image Analysis},
  Year = {2023},
  Volume = {89},
  Pages = {102889},
}
```

## Contact

If you have any problems about the WHS++ track, please contact [Dr. Wangbin Ding](mailto:dingwangbin@fjmu.edu.cn) or [Xicheng Sheng](mailto:xcsheng22@m.fudan.edu.cn).
