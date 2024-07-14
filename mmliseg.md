---
layout: distill
title: MMLiSeg
description: Multi-modality Liver Segmentation Challenge
permalink: /mmliseg/
toc:
  - name: Motivation
  - name: Task
  - name: Data
  - name: Metrics and Award
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

<div style="text-align: center;">
{% include figure.liquid loading="eager" path="/assets/img/mmliseg.png" class="img-fluid" max-width="500px" zoomable=true %}
</div>


## Motivation

The liver, being the largest solid organ in the human body, is crucial for metabolism and digestion. Accurate and precise segmentation of liver is essential for diagnosing cancer, planning treatment, and monitoring treatment response. However, current deep learning practice has poor generalizability facing domain shifts, that is, when deep learning models are evaluated on unseen datasets with different imaging modalities, the accuracy of segmentation can significantly decrease. This challenge, Multi-modality Liver Segmentation Challenge (MMLiSeg), aims to contribute to the effort of motivate participants to create generalizable automatic segmentation algorithms that can accurately segmentation across imaging modalities.

## Task

MMLiSeg targets to generalizable segmentation methods for Liver segmentation in different modalities, including T1, T2 and DWI MRIs. There are three phases, i.e., training, validation and test phases. In the training phase, T1 and T2 MRI data are provided. In the validation phase, T1, T2 and DWI data are used for hyperparameters selection. While in the test phase, the submitted algorithms of participants are finally evluated on T1, T2 and DWI data. 

## Data

### Data acquisition information

We include 180+ multi-modalities MRIs (.nii.gz) with manual segmentation of the liver region. All these clinical data have got institutional ethic approval and have been anonymized (please follow the data usage agreement).  
The details of the dataset are summarized as below:

<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:100%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Modality</th>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. studies</th>
      <th class="text-center" scope="col">Num. slices</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">T1</td>
      <td class="text-center">1</td>
      <td class="text-center">62</td>
      <td class="text-center">3031</td>
    </tr>
    <tr>
      <td class="text-center">T2</td>
      <td class="text-center">1</td>
      <td class="text-center">62</td>
      <td class="text-center">1675</td>
    </tr>
    <tr>
      <td class="text-center">DWI</td>
      <td class="text-center">1</td>
      <td class="text-center">64</td>
      <td class="text-center">1540</td>
    </tr>
  </tbody>
</table>
</div>



### Data split

The dataset has been divided into three main parts: training, validation, and test sets:

- **Training Set**: 37 T1 and 37 T2 MRIs 
- **Validation Set**: 12 T1,  12 T2 and 19 DWI MRIs
- **Test Set**: 13 T1,  13 T2 and 45 DWI MRIs



## Metrics and Award

### Metrics

The performance of scar and edema segmentation results will be evaluated by：

- *Dice Similarity Coefficient (DSC)*
- *Hausdorff Distance (HD)*
- *Average Surface Distance (ASD)*

### Award

The performance will be evaluated based on the of the submitted models. The best work will be selected with awards. Specifically, we will prepare one **Champion Winner Award**. 

## Registration

To access the dataset, please [sign up](http://zmic.org.cn/care_2024/eval/register?track=MMLiSeg) to participate in the challenge and get access to the dataset.

## Submission Guidance

### Model Submission

After registration, we will assign the participant an account to login into our [evaluation platform](http://zmic.org.cn/). Participants can directly upload your predictions on the validation data (in nii.gz format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/test_submission) for testing.

## Timeline
The schedule for this track is as follows. All deadlines are on 12:00 pm in Pacific Standard Time.

<table class="table table-sm table-hover border-bottom">
    <tr>
    <td><strong>Training Data Release</strong></td>
    <th scope="row" style="width: 60%" class="text-right">June 1, 2024</th>
    </tr>
    <tr>
    <td><strong>Validation Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">August 1, 2024 to September 1, 2024 (DDL)</th>
    </tr>
    <tr>
    <td><strong>Test Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">September 1, 2024 to October 1, 2024 (DDL)</th>
    </tr>
    <tr>
    <td><strong>Notification</strong></td>
    <th scope="row" style="width: 60%" class="text-right">October 5 </th>
    </tr>
    <tr>
    <td><strong>Workshop (Half-Day)</strong></td>
    <th scope="row" style="width: 60%" class="text-right">November 8, 2024</th>
    </tr>
</table>



## Citations
Please cite these papers when you use the data for publications:
```bib
@inproceedings{gao2023reliable,
  title={A reliable and interpretable framework of multi-view learning for liver fibrosis staging},
  author={Gao, Zheyao and Liu, Yuanye and Wu, Fuping and Shi, Nannan and Shi, Yuxin and Zhuang, Xiahai},
  booktitle={International Conference on Medical Image Computing and Computer-Assisted Intervention},
  pages={178--188},
  year={2023},
}

@misc{liu2024merit,
  title={MERIT: Multi-view Evidential learning for Reliable and Interpretable liver fibrosis sTaging}, 
  author={Yuanye Liu and Zheyao Gao and Nannan Shi and Fuping Wu and Yuxin Shi and Qingchao Chen and Xiahai Zhuang},
  year={2024},
  archivePrefix={arXiv},
}
```

## Organizer

- [Xiahai Zhuang](https://zmiclab.github.io/zxh/), School of Data Science, Fudan University
- Bomin Wang, School of Data Science, Fudan University

## Contact

If you have any questions regarding the MMLiSeg challenge, please feel free to contact:

- Bomin Wang: [21110980022@m.fudan.edu.cn](mailto:21110980022@m.fudan.edu.cn)
- Yibo Gao (contact person for IT support): [ybgao22@m.fudan.edu.cn](mailto:ybgao22@m.fudan.edu.cn)
- Zhen Zhang (contact person for IT support): [jmbbruce@163.com](mailto:jmbbruce@163.com)
