---
layout: distill
title: Weak MyoPS
description: Weakly Supervised Myocardial Pathology Segmentation
permalink: /weak_myops/
toc:
  - name: Motivation
  - name: Task
  - name: Data 
  - name: Metrics
  - name: Rules
  - name: Registration
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
{% include figure.liquid loading="eager" path="/assets/img/weak_myops.png" class="img-fluid" zoomable=true caption="Figure 1. Fully supervised and weakly supervised myocardial pathology segmentation." %}


Myocardial infarction is a common and serious cardiovascular disease that leads to necrosis and scar formation in cardiac tissues, significantly impacting patients' quality of life and health. Utilizing cardiac magnetic resonance (CMR) imaging techniques, particularly the late gadolinium enhancement (LGE) sequence, allows for the visualization of infarcted scar regions within the myocardium. However, manual segmentation of infarcted scars from LGE images is a time-consuming and labor-intensive task, while automated segmentation methods can enhance efficiency and reduce human error. 

As shown in Figure 1, traditional fully supervised deep learning methods require a large amount of accurately labeled data for training, which is often challenging and expensive. Weakly supervised learning methods, which aim to train models with limited supervision, have emerged as a promising solution to these challenges. By utilizing only **partial** or **noisy** labels, weakly supervised methods enable the training of deep learning models with reduced reliance on expensive and labor-intensive annotation efforts. 



## Task

Through this challenge, we aim to encourage participants to explore and develop novel weakly supervised deep learning methods for accurate segmentation of myocardial infarcted scars from LGE images with limited supervision. Additionally, we encourage participants to tackle the challenge of incorporating multi-center data, recognizing the importance of addressing real-world complexities to enhance the robustness and applicability of their proposed solutions.


The best works, following the precedent of [MyoPS 2020](https://zmiclab.github.io/zxh/0/myops20/), will be recognized with awards. Works are evaluated based on several key criteria: **Test Results**, **Novelty of Methodologies** and **Quality of the Manuscript**. 


## Data

This challenge will provide LGE for 300 patients across 6 centers from China, France, and the United Kingdom. Traced with lines in LGE to indicate scarred areas.



All clinical data have received institutional ethical approval and have been anonymized to ensure privacy and compliance with ethical standards. 


<table class="table table-sm table-hover border-bottom">
  <thead>
    <tr>
      <th scope="col">Center</th>
      <th scope="col">Num. patients</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>181</td>
    </tr>
    <tr>
      <td>B</td>
      <td>50</td>
    </tr>
    <tr>
      <td>C</td>
      <td>45</td>
    </tr>
    <tr>
      <td>D</td>
      <td>07</td>
    </tr>
    <tr>
      <td>E</td>
      <td>09</td>
    </tr>
    <tr>
      <td>F</td>
      <td>08</td>
    </tr>
  </tbody>
</table>

### Data Split

The dataset is divided into three main parts: training, validation, and test sets:

- **Validation Set**: 50 LGE from Center A.
- **Test Set**: 50 LGE from Center A.
- **Training Set**: The rest LGE from Centers A, B, C, E, F, and G.



### Data Format
LGE and line label of scars will be provided in the NIfTI format as follows:
- [Patient Identifier]_LGE.nii.gz
- [Patient Identifier]_Line.nii.gz


## Metrics

The performance of scar and edema segmentation results will be evaluated by：
- **Dice Similarity Coefficient (DSC)**
- **Accuracy (ACC)**
- **Sensitivity (SEN)**

Note that the track will provide an open platform for research groups to [validate](http://zmic.org.cn/) and [test](http://zmic.org.cn/) their methods. For a fair comparison, the test dataset will remain unseen. Participants need to submit their [docker container](http://zmic.org.cn/) to our platform for testing.


## Rules
- **Only automatic methods are acceptable.** Participants must utilize algorithms that do not require manual intervention or human-assisted processes for the segmentation task.
- **External data sets and pre-trained models are not allowed in this track.** The solutions must be developed using only the data provided within the scope of this track and cannot leverage any external datasets or models for assistance.


## Registration
Please [**sign up**](http://zmic.org.cn/) to join this track.

## Submission Guidance

### Model Submission
After registration, we will assign participants an account to log into our [evaluation platform](http://zmic.org.cn/). Participants can directly upload their predictions on the validation data (in NIfTI format) via the website. Note that evaluation of validation data will be allowed up to 10 times for each task per team. For a fair comparison, the test dataset will remain unseen. Participants need to submit their [docker models](http://zmic.org.cn/) for testing.



## Timeline
The schedule for this track is as follows. All deadlines(DDLs) are at 23:59 in Pacific Standard Time.

<table class="table table-sm table-hover border-bottom">
    <tr>
    <td class="text-left"><strong>Training Data Release</strong></td>
    <th scope="row" style="width: 60%" class="text-right">May 10, 2024</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Validation Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">June 10, 2024 to July 7, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Test Phase</strong></td>
    <th scope="row" style="width: 60%" class="text-right">July 7, 2024 to August 7, 2024 (DDL)</th>
    </tr>
    <tr>
    <td class="text-left"><strong>Abstract Submission</strong></td>
    <th scope="row" style="width: 60%" class="text-right">July 15, 2024 (DDL)</th>
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

If you have any questions regarding the challenge, please feel free to contact:

- Dr. Wangbin Ding: [dingwangbin@fjmu.edu.cn](mailto:dingwangbin@fjmu.edu.cn)
- Sihan Wang: [21110980009@m.fudan.edu.cn](mailto:21110980009@m.fudan.edu.cn)
- Yang Zhang: [zhangyang23@m.fudan.edu.cn](mailto:zhangyang23@m.fudan.edu.cn)
