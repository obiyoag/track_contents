---
layout: distill
title: MyoPS++
description: Myocardial Pathology Segmentation
permalink: /track4/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Task
  - name: Data 
  - name: Metrics
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
{% include figure.liquid loading="eager" path="/assets/img/myops.png" class="img-fluid" zoomable=true caption="Figure 1. Myocardial pathology segmentation and its challenges. (A) Myocardial Pathology Segmentation: Scar and edema regions are marked in green and yellow, respectively. (B) Challenges of Myocardial Pathology Segmentation: The challenges include multi-center data, missing sequences, and misalignments in multi-sequence CMR images." %}

Myocardial infarction (MI) is a major cause of mortality and disability worldwide. Assessment of myocardial viability is essential in the diagnosis and treatment management of MI patients <d-cite key="myops1"></d-cite>. Multi-sequence cardiac magnetic resonance (MS-CMR) images can provide valuable myocardial pathology information, which is important for the diagnosis and treatment management of patients. As shown in Figure 1 (A), balanced steady-state free precession (bSSFP) cine sequences present clear anatomical boundaries, while late gadolinium enhancement (LGE) and T2-weighted (T2) CMR sequences visualize myocardial scar and edema of MI, respectively.

## Task

The target of this track is to segment myocardial pathology regions, specifically scar and edema, from multi-sequence CMR data. This track seeks innovative solutions to address MyoPS using real-world multi-sequence CMR data. We encourage participants to overcome challenges such as the inclusion of multi-center data, missing sequences for some centers <d-cite key="myops2"></d-cite>, and misalignments in multi-sequence CMRs <d-cite key="myops3"></d-cite>, as illustrated in Figure 1 (B).

The best works, following the precedent of [MyoPS 2020](https://zmiclab.github.io/zxh/0/myops20/), will be recognized with awards. A work is assessed based on several key criteria: **Test Results**, **Generalizability of Methodologies** and **Quality of the Manuscript**. The selected papers will be published in our proceedings [see previous proceedings](https://link.springer.com/book/10.1007/978-3-030-65651-5).

Topics may cover (not exclusively):
- Myocardial Pathology Segmentation
- Cardiac Anatomy Segmentation
- Multi-Sequence Image Registration


## Data

This track will provide data of 250 patients across 7 centers from China, France, and the United Kingdom. The number of CMR sequence among the patients is as follows:

- **145 patients** have three CMR sequences: LGE, T2, and bSSFP.
- **24 patients** have two sequences: bSSFP and LGE.
- **81 patients** have only one sequence: LGE.

The LGE and T2 CMR sequences are respectively delineated with:
- **Scar** (2221)
- **Edema** (1220)

Additionally, we also provide labels for:
- **Left ventricle** (500)
- **Right ventricle** (600)
- **Healthy myocardium** (200)

All clinical data have received institutional ethical approval and have been anonymized to ensure privacy and compliance with ethical standards. 


<table class="table table-sm table-hover border-bottom">
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
      <td>A</td>
      <td>81</td>
      <td>LGE</td>
      <td>Scar, left ventricle and myocardium</td>
    </tr>
    <tr>
      <td>B</td>
      <td>50</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle, myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>C</td>
      <td>45</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle, myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>D</td>
      <td>50</td>
      <td>LGE, T2 and bSSFP</td>
      <td>Scar, edema, left ventricle, myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>E</td>
      <td>07</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle, myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>F</td>
      <td>09</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle, myocardium and right ventricle</td>
    </tr>
    <tr>
      <td>G</td>
      <td>08</td>
      <td>LGE and bSSFP</td>
      <td>Scar, left ventricle, myocardium and right ventricle</td>
    </tr>
  </tbody>
</table>

### Data Split

The dataset is divided into three main parts: training, validation, and test sets:

- **Training Set**: All patients from Centers A, B, C, E, F, and G.
- **Validation Set**: 25 patients from Center D.
- **Test Set**: 25 patients from Center D.

### Pre-Processing

In this track, LGE and T2 images are derived from the end-diastolic phase of the cardiac cycle. We have therefore extracted the end-diastolic phase of bSSFP (C0) for this track. 
Note that LGE, T2, and C0 are initially unaligned. The data published here come in two versions: one version has been pre-aligned using the [MvMM method](https://zmiclab.github.io/zxh/0/zxhproj), and another one has remained unaligned. **The test phase will be based on the version that has been aligned with the MvMM method.**

### Data Format
Each CMR sequence and gold standard label of patients will be provided in the NIfTI format as follows:
- [Patient Identifier]_LGE.nii.gz
- [Patient Identifier]_T2.nii.gz
- [Patient Identifier]_C0.nii.gz
- [Patient Identifier]_gd.nii.gz (gold standard label)

## Metrics

The performance of scar and edema segmentation results will be evaluated by：
- **Dice Similarity Coefficient (DSC)**
- **Precision (PRE)**
- **Sensitivity (SEN)**
- **Specificity (SPE)**

Note that the track will provide an open platform for research groups to [validate](http://zmic.org.cn/care_2024/eval/scoreboard?track=MyoPS%2B%2B) and [test](http://zmic.org.cn/care_2024/test_submission) their methods. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/docker_tutorial) to our platform for testing.

<!-- 
### Ranking

The best work, following the precedent of [MyoPS 2020](https://zmiclab.github.io/zxh/0/myops20/), will be recognized with awards. A work is assessed based on several key criteria:**Test Results**, **Ggeneralizability of Methodologies** and **Quality of the Manuscript**.

- **Test Results**: The performance of the methods as demonstrated by the test outcomes.
- **Novelty of Methodologies**: The originality and **generalizability** in the proposed methods.
- **Quality of the Manuscript**: The clarity, organization, and correctness of the written submission. The selected papers will be published in our proceedings [see previous proceedings](https://link.springer.com/book/10.1007/978-3-030-65651-5). 
- **Presentation of Their Paper**: The effectiveness of the oral or poster presentation in conveying the work.

-->

## Rules
- **Only automatic methods are acceptable.** Participants must utilize algorithms that do not require manual intervention or human-assisted processes for the segmentation task.
- **External data sets and pre-trained models are not allowed in this track.** The solutions must be developed using only the data provided within the scope of this track and cannot leverage any external datasets or models for assistance.


## Registration
Please [**sign up**](http://zmic.org.cn/care_2024/eval/register?track=MyoPS%2B%2B) to join this track.

## Submission Guidance

### Model Submission
After registration, we will assign participants an account to login into our [MyoPS++ evaluation platform](http://zmic.org.cn/care_2024/eval/login?track=MyoPS%2B%2B). Participants can directly upload your predictions on the validation data (in nifty format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/care_2024/test_submission) for testing.
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
    <th scope="row" style="width: 60%" class="text-right"> July 15 to August 15, 2024 (DDL)</th>
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
 @article{zhuang2019multivariate,
    title={Multivariate mixture model for myocardial segmentation combining multi-source images},
    author={Zhuang, Xiahai},
    journal={IEEE transactions on pattern analysis and machine intelligence},
    volume={41},
    number={12},
    pages={2933--2946},
    year={2019},
}

@article{li2023myops,
  title={MyoPS: A benchmark of myocardial pathology segmentation combining three-sequence cardiac magnetic resonance images},
  author={Li, Lei and Wu, Fuping and Wang, Sihan and Luo, Xinzhe and Mart{\'\i}n-Isla, Carlos and Zhai, Shuwei and Zhang, Jianpeng and Liu, Yanfei and Zhang, Zhen and Ankenbrand, Markus J and others},
  journal={Medical Image Analysis},
  volume={87},
  pages={102808},
  year={2023},
  publisher={Elsevier}
}

@article{qiu2023myops,
  title={MyoPS-Net: Myocardial pathology segmentation with flexible combination of multi-sequence CMR images},
  author={Qiu, Junyi and Li, Lei and Wang, Sihan and Zhang, Ke and Chen, Yinyin and Yang, Shan and Zhuang, Xiahai},
  journal={Medical image analysis},
  volume={84},
  pages={102694},
  year={2023},
}

 @article{ding2023aligning,
  title={Aligning multi-sequence CMR towards fully automated myocardial pathology segmentation},
  author={Ding, Wangbin and Li, Lei and Qiu, Junyi and Wang, Sihan and Huang, Liqin and Chen, Yinyin and Yang, Shan and Zhuang, Xiahai},
  journal={IEEE Transactions on Medical Imaging},
  year={2023},
}
```

## Contact

If you have any questions regarding the MyoPS++ track, please feel free to contact:

- Dr. Wangbin Ding: [dingwangbin@fjmu.edu.cn](mailto:dingwangbin@fjmu.edu.cn)
- Sihan Wang: [21110980009@m.fudan.edu.cn](mailto:21110980009@m.fudan.edu.cn)
- Yang Zhang: [zhangyang23@m.fudan.edu.cn](mailto:zhangyang23@m.fudan.edu.cn)


