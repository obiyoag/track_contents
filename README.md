---
layout: distill
title: TFM4MedIA
description: Transferring Foundation Models for Multi-center Real-World Medical Image Analysis
permalink: /track1/
bibliography: reference.bib
toc:
  - name: Important Dates
  - name: Motivation
  - name: Task
  - name: Registration
  - name: Data Overview
  - name: Metrics & Ranking
  - name: Rules
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

## Important Dates

The schedule for this track is as follows. All deadlines (DDL) are in Pacific Standard Time.

<table class="table table-sm table-hover border-bottom">
    <tr>
    <td><strong>Training Data Release</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
    <tr>
    <td><strong>Validation Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
    <tr>
    <td><strong>Test Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
  <tr>
    <td><strong>Abstract Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
  <tr>
    <td><strong>Paper Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
  <tr>
    <td><strong>Notification</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
  <tr>
    <td><strong>Camera Ready</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
  <tr>
    <td><strong>Workshop (Half-Day)</strong></td>
    <th scope="row" style="width: 60%" class="text-right">TBD</th>
    </tr>
</table>

## Motivation

{% include figure.liquid loading="eager" path="/assets/img/tfm4media.png" class="img-fluid" zoomable=true %}

While foundation models like the Segment Anything Model (SAM)<d-cite key="tfm1"></d-cite> have demonstrated efficacy in various medical image analysis tasks, their performance on real-world data remains underexplored. Specifically, these models are typically trained for normal and large targets such as the liver and lungs, yet real-world data often originates from different centers with diverse modalities. Furthermore, the application of foundation models to complicated Regions of Interest (ROIs), like lesions or scars, poses additional challenges due to their small size and irregular shapes. Hence, developing effective and efficient transfer learning approaches to fully utilize those foundation models for real world medical image segmentation is of great values.

## Task

In this track, we encourage participants to design effective transfer learning approaches to exploit the knowledge from existed foundation models efficiently and make them more effective in four segmentation tasks, including **Myocardial Pathology Segmentation** in [MyoPS++](http://zmic.org.cn/care_2024/track4/) track, **Liver Segmentation** in [LiFS](http://zmic.org.cn/care_2024/track3/) track, **Whole Heart Segmentation** in [WHS++](http://zmic.org.cn/care_2024/track5/) track and **Left Atrial and Scar Segmentation** in [LAScarQS++](http://zmic.org.cn/care_2024/track2/) track. 

***Note***: To address this task, participants are encouraged to leverage *external data*.

## Registration
Please register [here](http://zmic.org.cn/care_2024/eval/register?track=TFM4MedIA) to participate in the challenge and get access to the dataset!

## Data Overview

Multi-center datasets are provided for four sub-tasks. More detailed data information can be found here for [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/), [Liver Segmentation](http://zmic.org.cn/care_2024/track3/), [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/) and [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/).

### Training Dataset
*Note: Only **points** or **rectangular frames** are acceptable as **Prompts***. 

 1. [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Sequences</th>
      <th class="text-center" scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">1</td>
      <td class="text-center">81</td>
      <td class="text-center">LGE</td>
      <td class="text-center">Scar, left ventricle and  myocardium</td>
    </tr>
    <tr>
      <td class="text-center">2</td>
      <td class="text-center">50</td>
      <td class="text-center">LGE, T2 and bSSFP</td>
      <td class="text-center">Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
    <tr>
      <td class="text-center">3</td>
      <td class="text-center">45</td>
      <td class="text-center">LGE, T2 and bSSFP</td>
      <td class="text-center">Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
    <tr>
      <td class="text-center">5</td>
      <td class="text-center">07</td>
      <td class="text-center">LGE and bSSFP</td>
      <td class="text-center">Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
    <tr>
      <td class="text-center">6</td>
      <td class="text-center">09</td>
      <td class="text-center">LGE and bSSFP</td>
      <td class="text-center">Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
    <tr>
      <td class="text-center">7</td>
      <td class="text-center">08</td>
      <td class="text-center">LGE and bSSFP</td>
      <td class="text-center">Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>


 2. [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)
    
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Vendor</th>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. studies</th>
      <th class="text-center" scope="col">Num. Annotations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">1</td>
      <td class="text-center">100</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">2</td>
      <td class="text-center">100</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">3</td>
      <td class="text-center">50</td>
      <td class="text-center">10</td>
    </tr>
  </tbody>
</table>
</div>

 3. [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">20</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">20</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">C/D</td>
      <td class="text-center">20</td>
      <td class="text-center">MRI</td>
    </tr>
    <tr>
      <td class="text-center">E</td>
      <td class="text-center">26</td>
      <td class="text-center">MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4. [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Modality</th>
      <th class="text-center" scope="col">Num. task1</th>
      <th class="text-center" scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">3</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">60</td>
      <td class="text-center">130</td>
    </tr>

  </tbody>
</table>
</div>

*Note: **points** or **rectangular frames** for each class are provided as **Prompts**. Participants can generate prompts based on the segmentation ground truth by themselves*. 

### Validation Dataset

 1. [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Sequences</th>
      <th class="text-center" scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">4</td>
      <td class="text-center">25</td>
      <td class="text-center">LGE, T2 and bSSFP</td>
      <td class="text-center">Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>
 2. [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)

<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Vendor</th>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. studies</th>
      <th class="text-center" scope="col">Num. Annotations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">1</td>
      <td class="text-center">10</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">2</td>
      <td class="text-center">10</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">3</td>
      <td class="text-center">10</td>
      <td class="text-center">10</td>
    </tr>
  </tbody>
</table>
</div>

 3. [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">20</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">10</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">C/D</td>
      <td class="text-center">20</td>
      <td class="text-center">MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4. [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Modality</th>
      <th class="text-center" scope="col">Num. task1</th>
      <th class="text-center" scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
     <tr>
      <td class="text-center">2.1</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">0</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">3</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">10</td>
      <td class="text-center">10</td>
    </tr>
   

  </tbody>
</table>
</div>
*Note: **points** or **rectangular frames** for each class are provided as **Prompts**. Participants can generate prompts by themselves*. 
### Test Dataset

 1. [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Sequences</th>
      <th class="text-center" scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">4</td>
      <td class="text-center">25</td>
      <td class="text-center">LGE, T2 and bSSFP</td>
      <td class="text-center">Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>
 2. [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)

The 160 test cases corresponded to 120 new cases from the vendors provided in the training set and 40 additional cases from a third unseen centre, that were tested for model generalizability. 

<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:50%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Vendor</th>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. studies</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">1</td>
      <td class="text-center">40</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">2</td>
      <td class="text-center">40</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">3</td>
      <td class="text-center">40</td>
    </tr>
    <tr>
      <td class="text-center">C (new)</td>
      <td class="text-center">4</td>
      <td class="text-center">40</td>
    </tr>
  </tbody>
</table>
</div>


 3. [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Num. patients</th>
      <th class="text-center" scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td class="text-center">A</td>
      <td class="text-center">20</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">B</td>
      <td class="text-center">14</td>
      <td class="text-center">CT</td>
    </tr>
    <tr>
      <td class="text-center">C/D</td>
      <td class="text-center">20</td>
      <td class="text-center">MRI</td>
    </tr>
    <tr>
      <td class="text-center">F</td>
      <td class="text-center">16</td>
      <td class="text-center">MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4. [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th class="text-center" scope="col">Center</th>
      <th class="text-center" scope="col">Modality</th>
      <th class="text-center" scope="col">Num. task1</th>
      <th class="text-center" scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
     <tr>
      <td class="text-center">1</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">0</td>
      <td class="text-center">20</td>
    </tr>
    <tr>
      <td class="text-center">2.1</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">0</td>
      <td class="text-center">10</td>
    </tr>
    <tr>
      <td class="text-center">2.2</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">0</td>
      <td class="text-center">40</td>
    </tr>
    <tr>
      <td class="text-center">3</td>
      <td class="text-center">LGE MRI</td>
      <td class="text-center">24</td>
      <td class="text-center">14</td>
    </tr>
   

  </tbody>
</table>
</div>
*Note: for testing, no more than 5 points and 1 rectangular frame are used by organizers for each class as prompts*. 
## Metrics & Ranking

### Metrics

Dice Similarity Coefficient (DSC), Hausdorff Distance

### Rank methods

The overall performance across all sub-tasks are considered for ranking: 
1) Firstly, for each sub-task, the results will be ranked according to the Dice score on in-distribution (seen centre) and out-of-distribution (OOD, unseen centre) dataset, respectively.
2) Then the ranking results of all sub-tasks are averaged as the final rank.

This ranking approach encourage the participants to develop methods from foundation models to be consistently effective across all tasks as well as on OOD datasets.

## Rules

1. Publicly available data and pretrained model are allowed. 


## Citations
**Please cite these papers when you use the data for publications:**
```bib
@article{Wu2023SemiSL,
  author={Wu, Fuping and Zhuang, Xiahai},
  journal={IEEE Transactions on Pattern Analysis and Machine Intelligence}, 
  title={Minimizing Estimated Risks on Unlabeled Data: A New Formulation for Semi-Supervised Medical Image Segmentation}, 
  year={2023},
  volume={45},
  number={5},
  pages={6021-6036},
}

@article{GAO2023BayeSeg,
  title = {BayeSeg: Bayesian modeling for medical image segmentation with interpretable generalizability},
  journal = {Medical Image Analysis},
  volume = {89},
  pages = {102889},
  year = {2023},
  author = {Shangqi Gao and Hangqi Zhou and Yibo Gao and Xiahai Zhuang},
}
```

## Contact

If you have any problems about this track, please contact [Dr. Fuping Wu](fuping_wu@outlook.com) or [Dr. Shangqi Gao](18110980005@fudan.edu.cn).
