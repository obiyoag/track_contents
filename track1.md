---
layout: distill
title: TFM4MedIA
description: Transferring Foundation Models for Multi-center Real-World Medical Image Analysis
permalink: /track1/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Task
  - name: Data
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

{% include figure.liquid loading="eager" path="/assets/img/tfm4media.png" class="img-fluid" zoomable=true caption="Figure 1." %}

While foundation models like the Segment Anything Model (SAM)<d-cite key="tfm1"></d-cite> have demonstrated efficacy in various medical image analysis tasks, their performance on real-world data remains underexplored. Specifically, these models are typically trained for normal and large targets such as the liver and lungs, yet real-world data often originates from different centers with diverse modalities. Furthermore, the application of foundation models to complicated Regions of Interest (ROIs), like lesions or scars, poses additional challenges due to their small size and irregular shapes. Hence, developing effective and efficient transfer learning approaches to fully utilize those foundation models for real world medical image segmentation is of great values.

## Task

In this track, we encourage participants to design effective transfer learning approaches to exploit the knowledge from existed foundation models efficiently and make them more effective in four segmentation tasks, including **Myocardial Pathology Segmentation** in [MyoPS++](http://zmic.org.cn/care_2024/track4/) track, **Liver Segmentation** in [LiQA](http://zmic.org.cn/care_2024/track3/) track, **Whole Heart Segmentation** in [WHS++](http://zmic.org.cn/care_2024/track5/) track and **Left Atrial and Scar Segmentation** in [LAScarQS++](http://zmic.org.cn/care_2024/track2/) track. 

***Note***: To address this task, participants are encouraged to leverage *external data*.


## Data

Multi-center datasets are provided for four sub-tasks. More detailed data information can be found here for [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/), [Liver Segmentation](http://zmic.org.cn/care_2024/track3/), [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/) and [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/).

### Training Dataset

1). [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Sequences</th>
      <th scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>81</td>
      <td>LGE</td>
      <td>Scar, left ventricle and  myocardium</td>
    </tr>
    <tr>
      <td>2</td>
      <td>50</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>3</td>
      <td>45</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>5</td>
      <td>07</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
    <tr>
      <td>6</td>
      <td>09</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
    <tr>
      <td>7</td>
      <td>08</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle,  myocardium and and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>


 2). [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)
    
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Vendor</th>
      <th scope="col">Center</th>
      <th scope="col">Num. studies</th>
      <th scope="col">Num. Annotations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>A</td>
      <td>100</td>
      <td>10</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B1</td>
      <td>100</td>
      <td>10</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B2</td>
      <td>50</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


 3). [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>20</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>B</td>
      <td>20</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>C/D</td>
      <td>20</td>
      <td>MRI</td>
    </tr>
    <tr>
      <td>E</td>
      <td>26</td>
      <td>MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4). [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Modality</th>
      <th scope="col">Num. task1</th>
      <th scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>LGE MRI</td>
      <td>60</td>
      <td>130</td>
    </tr>

  </tbody>
</table>
</div>


### Validation Dataset

 1). [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Sequences</th>
      <th scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4</td>
      <td>25</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>

 2). [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)

<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Vendor</th>
      <th scope="col">Center</th>
      <th scope="col">Num. studies</th>
      <th scope="col">Num. Annotations</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>A</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B1</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B2</td>
      <td>10</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


 3). [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>20</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>B</td>
      <td>10</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>C/D</td>
      <td>20</td>
      <td>MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4). [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Modality</th>
      <th scope="col">Num. task1</th>
      <th scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
     <tr>
      <td>A</td>
      <td>LGE MRI</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <td>C</td>
      <td>LGE MRI</td>
      <td>0</td>
      <td>10</td>
    </tr>
  </tbody>
</table>
</div>


### Test Dataset

 1). [Myocardial Pathology Segmentation](http://zmic.org.cn/care_2024/track4/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Sequences</th>
      <th scope="col">Manual labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>4</td>
      <td>25</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle,  myocardium and right ventricle</td>
    </tr>
  </tbody>
</table>
</div>

 2). [Liver Segmentation](http://zmic.org.cn/care_2024/track3/)

The 160 test cases corresponded to 120 new cases from the vendors provided in the training set and 40 additional cases from a third unseen center, that were tested for model generalizability. 

<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:50%;align:center;">
  <thead>
    <tr>
      <th scope="col">Vendor</th>
      <th scope="col">Center</th>
      <th scope="col">Num. studies</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>A</td>
      <td>40</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B1</td>
      <td>40</td>
    </tr>
    <tr>
      <td>B</td>
      <td>B2</td>
      <td>40</td>
    </tr>
    <tr>
      <td>C (new)</td>
      <td>C</td>
      <td>40</td>
    </tr>
  </tbody>
</table>
</div>



 3). [Whole Heart Segmentation](http://zmic.org.cn/care_2024/track5/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
      <th scope="col">Modalities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>20</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>B</td>
      <td>14</td>
      <td>CT</td>
    </tr>
    <tr>
      <td>C/D</td>
      <td>20</td>
      <td>MRI</td>
    </tr>
    <tr>
      <td>F</td>
      <td>16</td>
      <td>MRI</td>
    </tr>
  </tbody>
</table>
</div>

 4). [Left Atrial and Scar Segmentation](http://zmic.org.cn/care_2024/track2/)
<div style="display: flex; justify-content: center;">
<table class="table table-sm table-hover border-bottom" style="table-layout:fixed;width:85%;align:center;">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Modality</th>
      <th scope="col">Num. task1</th>
      <th scope="col">Num. task2</th>
    </tr>
  </thead>
  <tbody>
     <tr>
      <td>A</td>
      <td>LGE MRI</td>
      <td>24</td>
      <td>14</td>
    </tr>
    <tr>
      <td>B</td>
      <td>LGE MRI</td>
      <td>0</td>
      <td>20</td>
    </tr>
<!--     <tr>
      <td>2.2</td>
      <td>LGE MRI</td>
      <td>0</td>
      <td>40</td>
    </tr> -->
    <tr>
      <td>C</td>
      <td>LGE MRI</td>
      <td>0</td>
      <td>10</td>
    </tr>
   

  </tbody>
</table>
</div>

### Prompts

<div style="text-align: center;">
  {% include figure.liquid loading="eager" path="/assets/img/tfm4media2.png" class="img-fluid" max-width="360px" zoomable=true caption="Figure 2. An example of acceptable prompts." %}
</div>

+ Only **points** or **bounding boxes** are acceptable as **prompts**. Participants can generate prompts based on the segmentation ground truth by themselves for the training dataset.
+ For validation and testing testing, no more than **5 points** and **1 bounding box** are provided by organizers for each class as prompts. An example can be seen in the Figure 2.

## Metrics & Ranking

### Metrics

Dice Similarity Coefficient (DSC), Hausdorff Distance (HD).

### Rank methods

The overall performance across all sub-tasks are considered for ranking: 
1) Firstly, for each sub-task, the results will be ranked according to the Dice score on in-distribution (seen centre) and out-of-distribution (OOD, unseen centre) dataset, respectively.
2) Then the ranking results of all sub-tasks are averaged as the final rank.

This ranking approach encourage the participants to develop methods from foundation models to be consistently effective across all tasks as well as on OOD datasets.

## Rules

1. Publicly available data and pretrained model are allowed. 


## Registration
Please register [here](http://zmic.org.cn/care_2024/eval/register?track=TFM4MedIA) to participate in the challenge and get access to the dataset!

## Submission Guidance

### Model Submission
After registration, we will assign participants an account to login into our [TFM4MedIA evaluation platform](http://zmic.org.cn/care_2024/eval/login?track=TFM4MedIA). Participants can directly upload your predictions on the validation data (in nifty format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/test_submission) for testing.
### Paper Submission
Please refer to our [paper submission guidance](/care_2024/paper_submission).

### Docker Submission (New!!!)
Since the aim of TM4MedIA is one model for all tasks, we make the name/directory/paths of a specific test task anonymous to avoid anyone using the information to select a specfiic model (e.g., nnUnet) for each test task. Therefore, we copy all test images of a specific task into the directory ":/input/images/" and save the corresponding prompts to the path ":/input/prompts.json". For convenience, the json structure keeps the same as the validation phase. For example, the structure of ":/input" is
```bash
:/input
    |-- prompts.json
    |-- images
        |-- Case ID1.nii.gz
        |-- Case ID2.nii.gz
        ...
        |__ Case IDN.nii.gz
```
**Note that** for MyoPS++, one case has three sequences, i.e., "Case ID*_C0.nii.gz", "Case ID*_LGE.nii.gz", and "Case ID*_T2.nii.gz".

The structure of ":/input/prompts.json" is
```json
{
    "Case ID1":
    {
        "Slice Id1": null,               #set to null if no/tiny foreground 
        ...
        "Slice IDk": 
        {
            "Label ID1": 
            [
                [x, y, x + h, y + w],     #bounding box prompt
                [[x1, y1],[x2, y2], ...]  #point prompt, the number of points ranges in [1,5]
            ]
            ...
        }
        ...
    }
    ...
}
```
**Orientations**: when apply prompts to images, the orientation of loading images should be set to `axcodes="PLS"`. 

Your docker should read the input test images from the directory ":/input/images", load the input prompts from the path ":/input/prompts.json", and output the corresponding predictions into the directory ":/output". The recommended structure of the directory ":/output" is
```bash
:/output
    |-- Case ID1_pred.nii.gz
    |-- Case ID2_pred.nii.gz
    ...
    |__ Case IDN_pred.nii.gz
```

The output segmentation should keep the same size as its original image/case. For the slices with null prompt, just label all areas as `Label ID=0`. For the slices with prompts, the label of segmentation should keep the same as the given label of prompts (`"Label ID"`). **Note that inconsistent labels would lead to incorrect evaluation.**

## Timeline
The schedule for this track is as follows. All deadlines(DDLs) are on 23:59 in Pacific Standard Time.

<table class="table table-sm table-hover border-bottom">
    <tr>
    <td class="text-left"><strong>Training Data Release</strong></td>
    <th scope="row" style="width: 60%" class="text-right">May 10, 2024</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Validation Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>June 10, 2024 to July 7, 2024 (DDL)</s> July 1, 2024 to September 25, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Test Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>July 7, 2024 to August 7, 2024 (DDL)</s> August 15, 2024 to September 15, 2024</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Abstract Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>July 15, 2024 (DDL) July 25, 2024 (DDL)</s> August 22, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Paper Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right"><s>August 15, 2024 (DDL)</s>September 1, 2024 (DDL)</th>
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

If you have any problems about this track, please contact [Dr. Fuping Wu](mailto:fuping_wu@outlook.com) or [Dr. Shangqi Gao](mailto:18110980005@fudan.edu.cn).
