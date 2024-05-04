---
layout: distill
title: LiQA
description: Liver Fibrosis Quantification and Analysis
permalink: /track3/
bibliography: reference.bib
toc:
  - name: Motivation
  - name: Data
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

## Motivation
{% include figure.liquid loading="eager" path="/assets/img/liqa1.png" class="img-fluid" zoomable=true caption="Figure 1." %}
Liver fibrosis, arising from chronic viral or metabolic liver conditions, presents a significant global health challenge. Precise **liver segmentation (LiSeg)** and **fibrosis staging (LiFS)**<d-cite key="liqa1"></d-cite> are essential for evaluating disease severity and facilitating accurate diagnoses. This task focuses on achieving 2 tasks, including automatic **liver segmentation** and **fibrosis staging** from **multi-phase** and **multi-center** liver MRI scans. Automatic LiSeg and LiFS face challenges including **random missing modalities** for certain patients, **misalignments** among multi-phase MRIs, and different modalities and domain shifts of multi-center data. Participants will strive to better integrate multi-phase information (optional for liver segmentation task) for achieving more **precise and generalizable** liver segmentation and fibrosis diagnoses. The LiSeg task aims to predict liver segmentation of Hepatobiliary phase MRI with **limited ground truth**, which is the most crutial phase for liver fibrosis staging. Moreover, the extensive use of **external data and pre-trained models are encouraged** in this track to support liver segmentation.

## Data

### About the data

**1) Scanner:** Philips Ingenia3.0T, Philips Ingenia3.0T, Siemens Skyra 3.0T, Siemens Aera 1.5T.

**2) Dataset overview:**  The track cohort was composed of **500 patients** diagnosed with liver fibrosis underwent multi-phase MRI scans. All subjects were scanned in clinical centres using three different magnetic resonance scanner vendors. The dataset will include **multi-phase** and **multi-center** data, consisting of T2-weighted imaging, diffusion-weighted imaging, and gadolinium ethoxybenzyl diethylenetriamine pentaacetic acid (Gd-EOB-DTPA)-enhanced dynamic MRIs. Gd-EOB-DTPA-enhanced dynamic MRIs: Includes non-contrast phase, arterial phase, venous phase, delay phase, and hepatobiliary phase.

**3) Contrast-enhanced dynamic scans:** Contrast-enhanced scans were performed based on the injection of GD-EOB-DTPA agent. The arterial phase was when the contrast agent entered the left ventricle, the portal phase was after 1min, the venous phase was after 90s, and the delay phase was after 3 min, and the hepatobiliary phase was after 20 min.

**4) Data format:** The data is all in Nifty format. Each sample may have 0-1 phase missing, and each modality has not been pre-aligned through spatial registration.

### Training Set

The training set contained 30 annotated segmentation images and 220 unannotated images from two different MRI vendors. Please note that all samples contain the gold standard for liver fibrosis staging. Liver fibrosis staging including 4 types of fibrosis severity. The hepatobiliary phase images have been segmented by experienced clinicians with liver region. 

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

### Validation Set

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

### Test Set

The 160 test cases corresponded to 120 new cases from the vendors provided in the training set and 40 additional cases from a third unseen vendor, that were tested for model generalizability. 

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
      <td class="text-center">C</td>
      <td class="text-center">4</td>
      <td class="text-center">40</td>
    </tr>
  </tbody>
</table>
</div>

## Metrics & Ranking

### Metrics

Classification: Area under curve (AUC); Accuracy;
Segmentation: Dice Similarity Coefficient (DSC), Hausdorff Distance

### Rank methods

The performance of classification and segmentation is ranged separately.
For classification, the average of metrics, i.e., Area under curve (AUC) and accuracy, is utilized to evaluate performance.
For segmentation, the average of metrics, i.e., Dice Similarity Coefficient (DSC) and Hausdorff Distance is utilized to  evaluate performance.

**==The average of accuracy and generalization accuracy is used for the final ranking==**

## Rules
1. Publicly available data (such as [LLD-MMRI2023](https://github.com/LMMMEng/LLD-MMRI2023)) and pretrained model are allowed. 
2. Only automatic methods are acceptable. 
