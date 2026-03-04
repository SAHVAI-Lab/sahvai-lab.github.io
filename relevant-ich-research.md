# Relevant ICH Research Articles

Research papers and resources related to intracranial hemorrhage (ICH) detection and classification using artificial intelligence, curated by the SAHVAI Lab.

---

## Deep Learning for Hemorrhagic vs. Ischemic Stroke Classification

### GCDCNet: Attention-Enhanced Deep Learning for Stroke CT Classification (2026) ⭐

**Che S, Che S, Liu X, Du P, Wang Z, Chen Y, Hu Y, Kong L**  
*Eur J Med Res.* 2026 Mar 3. doi: 10.1186/s40001-025-03784-w  
[PubMed](https://pubmed.ncbi.nlm.nih.gov/41776569/) | [DOI](https://doi.org/10.1186/s40001-025-03784-w)

#### Summary

This study presents **GCDCNet** (Ghost Convolution with Dilated Convolution and Channel Shuffling Network), a lightweight deep learning model achieving 99.26% accuracy in classifying hemorrhagic vs. ischemic stroke on CT imaging. The model combines:

- **GhostNet** lightweight backbone (2.7M parameters - 10x smaller than competitors)
- **SCSE** (Spatial & Channel Squeeze-Excitation) attention mechanism
- **Dilated convolution** for multi-scale feature extraction
- **Channel shuffling** for feature fusion
- **Grad-CAM visualization** for clinical interpretability

#### Key Performance Metrics

| Metric | Score |
|--------|-------|
| **Accuracy** | 99.26% |
| **Recall** | 99.33% |
| **Precision** | 98.94% |
| **F1 Score** | 99.13% |
| **AUC-ROC** | 0.9996 |
| **Parameters** | 2.7M (lightweight) |
| **Inference Speed** | Real-time capable |

Outperformed ConvNeXt, EfficientNet, GhostNet, HRNet, and ViT on the same dataset.

#### Clinical Applications

- ✅ Early stroke screening in emergency departments
- ✅ Automated triage for hemorrhagic vs. ischemic classification
- ✅ Telemedicine support for remote/rural hospitals
- ✅ Point-of-care deployment (lightweight architecture)
- ✅ Medical resource optimization

#### Technical Highlights

**SCSE Attention Mechanism:**
- Combines spatial attention (where lesions are) + channel attention (which features matter)
- Guides model to focus on clinically relevant hemorrhage/ischemia regions
- Mimics radiologist visual search patterns

**Grad-CAM Interpretability:**
- Visualization shows model discrimination areas highly consistent with clinician focus
- Essential for clinical trust and validation
- Enables explainable AI in emergency decision-making

#### Relevance to SAHVAI Lab

**Integration Opportunities:**
1. **Attention mechanisms** could enhance SAHVAI-3D hemorrhage localization
2. **Lightweight architecture** (2.7M params) enables edge deployment for SAH screening
3. **Grad-CAM approach** aligns with eSAH score clinical validation methodology
4. **Multi-task learning** potential: Classify stroke type + estimate SAH volume simultaneously

**Potential Workflow:**
```
CT Scan → GCDCNet Triage (hemorrhagic/ischemic)
         ↓
    If Hemorrhagic → SAHVAI-3D Volume Estimation
                   ↓
              eSAH Score → Prognosis
```

---

## Public Datasets for ICH Research

### 1. Brain Stroke Prediction CT Scan Image Dataset (Kaggle) 📊

**Used in GCDCNet study above**

**Dataset:** [Brain Stroke Prediction CT Scan Image Dataset](https://www.kaggle.com/datasets/noshintasnia/brain-stroke-prediction-ct-scan-image-dataset)

**Contents:**
- **964 hemorrhagic stroke** CT images
- **1,551 ischemic stroke** CT images
- **Total:** 2,515 CT scans
- Format: Preprocessed CT slices
- Labels: Binary classification (hemorrhagic vs. ischemic)

**Use Cases:**
- Training/validating stroke classification models
- Benchmarking deep learning architectures
- Testing attention mechanisms for lesion localization
- Educational purposes for medical AI research

**Access:** Free download via Kaggle (requires Kaggle account)

**Citation:** Che S, et al. (2026) used this dataset to achieve 99.26% classification accuracy with GCDCNet.

---

### 2. RSNA Intracranial Hemorrhage Detection Challenge 2019 🏆

**Dataset:** [RSNA ICH Detection Challenge](https://www.rsna.org/artificial-intelligence/ai-image-challenge/rsna-intracranial-hemorrhage-detection-challenge-2019)

**Contents:**
- **~25,000 CT slices** from emergency department patients
- **6 hemorrhage subtypes:**
  - Epidural
  - Intraparenchymal
  - Intraventricular
  - Subarachnoid ⭐ (relevant to SAHVAI)
  - Subdural
  - Any (combined)
- Multi-label classification (patients can have multiple hemorrhage types)
- Expert radiologist annotations

**Challenge Results:**
- Top models achieved ~0.93 AUC
- Demonstrated clinical-grade performance for ICH detection
- Published in *Radiology: Artificial Intelligence* (2020)

**Use Cases:**
- **SAH-specific model training** (subarachnoid hemorrhage subset)
- Multi-label hemorrhage classification
- Cross-validation with SAHVAI-3D volumetrics
- Comparing detection vs. volumetric approaches

**Access:**
- Dataset available on Kaggle: [RSNA ICH Challenge](https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection)
- Requires acceptance of data use agreement
- Free for research purposes

**Relevance to SAHVAI:**
- Contains **subarachnoid hemorrhage** (SAH) labels
- Could be used to:
  - Train SAH detection models complementary to SAHVAI-3D
  - Validate eSAH score on broader ICH population
  - Compare SAHVAI volumetrics against multi-label classification approaches

---

## Using These Datasets with SAHVAI Models

### Recommended Workflow

**For Stroke Classification (GCDCNet-style):**
1. Download [Kaggle Brain Stroke Dataset](https://www.kaggle.com/datasets/noshintasnia/brain-stroke-prediction-ct-scan-image-dataset)
2. Train lightweight classifier (hemorrhagic vs. ischemic)
3. Use as triage step before SAHVAI-3D volumetrics

**For SAH-Specific Research:**
1. Download [RSNA ICH Challenge](https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection)
2. Filter for **subarachnoid hemorrhage** labels
3. Compare SAHVAI-3D volume estimates with SAH detection labels
4. Validate eSAH score predictions against clinical outcomes

**For Multi-Center Validation:**
1. Combine both datasets for robust training
2. Test SAHVAI models on external validation sets
3. Benchmark against state-of-the-art (GCDCNet = 99.26% accuracy baseline)

---

## Related SAHVAI Publications

See [SAHVAI Lab Publications](papers.md) for our core research:
- SAHVAI-3D and 4D: Automated SAH volumetric measurement
- eSAH Score: Predictive model for SAH outcomes
- ABC/2 Method: Simplified SAH volume estimation

---

## Contributing

Found a relevant ICH/stroke AI paper? Contact us:
- **GitHub:** [SAHVAI-Lab](https://github.com/SAHVAI-Lab)
- **PI:** W. David Freeman, MD - freeman.william1@mayo.edu
- **Lab Website:** [SAHVAI Lab](https://sahvai-lab.github.io)

---

**Last Updated:** 2026-03-04  
**Curated by:** SAHVAI Lab, Mayo Clinic Jacksonville
