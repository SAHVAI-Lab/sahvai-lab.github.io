# GCDCNet Reference Implementation - Repo Proposal for SAHVAI GitHub

**Proposed Repo Name:** `SAHVAI-Lab/stroke-classification-attention`

---

## Why Create This?

The paper (PMID 41776569) presents **GCDCNet** with exceptional performance (99.26% accuracy) but **no public code repository**. SAHVAI Lab could:

1. ✅ Create a reference implementation for the community
2. ✅ Test attention mechanisms for SAHVAI-3D integration
3. ✅ Benchmark against Mayo stroke CT datasets
4. ✅ Demonstrate Mayo's AI leadership in stroke imaging

---

## Repository Structure

```
SAHVAI-Lab/stroke-classification-attention/
├── README.md                          # Overview, citation, results
├── LICENSE                            # MIT or Apache 2.0
├── requirements.txt                   # Dependencies
├── models/
│   ├── ghostnet.py                    # GhostNet backbone (from Huawei repo)
│   ├── scse_attention.py              # SCSE attention module
│   ├── gcdcnet.py                     # Full GCDCNet architecture
│   └── baseline_models.py             # ConvNeXt, EfficientNet comparisons
├── data/
│   ├── datasets.py                    # Dataset loaders
│   ├── augmentation.py                # Data augmentation pipeline
│   └── public_datasets.md             # Links to public stroke CT datasets
├── train.py                           # Training script
├── evaluate.py                        # Evaluation + Grad-CAM visualization
├── inference.py                       # Single-image inference
├── notebooks/
│   ├── demo_gradcam.ipynb             # Grad-CAM interpretability demo
│   └── performance_comparison.ipynb   # Model benchmarking
├── configs/
│   └── gcdcnet_config.yaml            # Hyperparameters from paper
└── checkpoints/
    └── README.md                      # Instructions for pre-trained weights
```

---

## Implementation Plan

### Phase 1: Core Architecture (Week 1)
- [ ] Implement GhostNet backbone (adapt from [huawei-noah/Efficient-AI-Backbones](https://github.com/huawei-noah/Efficient-AI-Backbones))
- [ ] Implement SCSE attention module (based on [cSE + sSE](https://arxiv.org/abs/1803.02579))
- [ ] Implement dilated convolution layers
- [ ] Implement channel shuffling module
- [ ] Unit tests for each component

### Phase 2: Training Pipeline (Week 2)
- [ ] Data loader for public stroke CT datasets (see below)
- [ ] Training script with Adam optimizer + cross-entropy loss
- [ ] Grad-CAM visualization integration
- [ ] TensorBoard logging

### Phase 3: Validation & Benchmarking (Week 3)
- [ ] Reproduce paper's metrics (99.26% accuracy target)
- [ ] Compare against baseline models (ConvNeXt, EfficientNet, etc.)
- [ ] Generate Grad-CAM heatmaps for clinical validation
- [ ] Document performance on Mayo internal dataset (if IRB approved)

### Phase 4: Documentation & Release (Week 4)
- [ ] Write comprehensive README with usage examples
- [ ] Create Jupyter notebook demos
- [ ] Add pre-trained weights (if available)
- [ ] Publish to SAHVAI-Lab GitHub

---

## Public Datasets (Mentioned in Paper)

The paper used **"public stroke CT dataset"** with:
- 964 hemorrhagic strokes
- 1,551 ischemic strokes
- **Total:** 2,515 images

### Likely Candidates:

1. **CQ500 Dataset** ([Qure.ai](http://headctstudy.qure.ai/dataset))
   - 491 CT scans with hemorrhage annotations
   - Publicly available for research

2. **RSNA Intracranial Hemorrhage Detection Challenge**
   - Kaggle dataset: ~25,000 CT slices
   - Multiple hemorrhage subtypes
   - [Link](https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection)

3. **PhysioNet Computed Tomography Medical Images**
   - Stroke CT scans with annotations
   - [Link](https://physionet.org/)

4. **GitHub Stroke Datasets:**
   - [AkramOM606/DeepLearning-CNN-Brain-Stroke-Prediction](https://github.com/AkramOM606/DeepLearning-CNN-Brain-Stroke-Prediction)
   - Contains preprocessed CT images

**Action:** Contact paper authors (Kong L - klb1984@163.com) to confirm which dataset they used.

---

## Reference Implementations (Building Blocks)

### GhostNet Backbone
- **Official PyTorch:** [huawei-noah/Efficient-AI-Backbones](https://github.com/huawei-noah/Efficient-AI-Backbones)
- **Alternative:** [iamhankai/ghostnet.pytorch](https://github.com/iamhankai/ghostnet.pytorch)
- License: MIT (commercial-friendly)

### SCSE Attention Module
- **Paper:** "Concurrent Spatial and Channel Squeeze & Excitation" ([arXiv:1803.02579](https://arxiv.org/abs/1803.02579))
- **Implementation:** Can adapt from existing SE-Net repos
- **Components:**
  - Spatial Squeeze-Excitation (sSE)
  - Channel Squeeze-Excitation (cSE)
  - Combined: SCSE = sSE + cSE

### Grad-CAM Visualization
- **Library:** `pytorch-grad-cam` ([jacobgil/pytorch-grad-cam](https://github.com/jacobgil/pytorch-grad-cam))
- Easy integration for interpretability

---

## Why SAHVAI Should Lead This

1. **Fill the Gap:** No public implementation exists yet (paper published Mar 3, 2026)
2. **Mayo Validation:** Benchmark on Mayo's internal stroke CT datasets
3. **Clinical Impact:** Demonstrate attention mechanisms for interpretable AI
4. **Research Pipeline:** Use as foundation for:
   - SAH vs. ischemic vs. hemorrhagic classification
   - Multi-task learning (classify + volumetrics)
   - Lightweight deployment (2.7M parameters = edge-ready)
5. **Community Contribution:** Advance open-source stroke AI research

---

## Timeline & Resources

**Duration:** 4 weeks (1 FTE researcher or distributed team)

**Skills Needed:**
- PyTorch deep learning
- Medical imaging (DICOM/NIfTI)
- Grad-CAM visualization

**Potential Collaborators:**
- SAHVAI Lab team (Sharma, Salman, Wei, Gu, Dherin, Reddy)
- Mayo AI Center
- Radiology residents (clinical validation)

---

## Success Metrics

✅ **Reproducibility:** Match paper's 99.26% accuracy on public dataset  
✅ **Interpretability:** Grad-CAM heatmaps align with radiologist annotations  
✅ **Performance:** <100ms inference time (lightweight deployment)  
✅ **Impact:** >50 GitHub stars, cited by other stroke AI papers  

---

## Alternative: Contact Authors First

**Before implementing from scratch, reach out to:**

**Lead Author:** Kong Lingbo  
**Email:** klb1984@163.com  
**Institution:** Institute for Brain Disorders, Beijing University of Chinese Medicine

**Email Template:**

> Subject: GCDCNet Code Request - Collaboration Opportunity (Mayo Clinic)
>
> Dear Dr. Kong,
>
> We read your excellent paper "Attention-enhanced deep learning model for automated classification of hemorrhagic and ischemic stroke on CT imaging" (PMID: 41776569) with great interest.
>
> I'm writing from the SAHVAI Lab at Mayo Clinic, where we develop AI models for stroke imaging (SAHVAI-3D/4D for SAH volumetrics, eSAH score). Your GCDCNet architecture, particularly the SCSE attention mechanism and lightweight design, is highly relevant to our work.
>
> **Questions:**
> 1. Is the GCDCNet source code publicly available? If not, would you be open to sharing it for research purposes?
> 2. Which public stroke CT dataset did you use (964 hemorrhagic + 1551 ischemic)?
> 3. Would you be interested in validating GCDCNet on Mayo's stroke CT datasets?
>
> We'd be happy to cite your work and potentially collaborate on a multi-center validation study.
>
> Best regards,  
> W. David Freeman, MD  
> Director, SAHVAI Lab  
> Mayo Clinic, Jacksonville, FL  
> freeman.william1@mayo.edu
>
> GitHub: https://github.com/SAHVAI-Lab

---

## Recommendation

**Step 1:** Email Kong L. to request code/dataset info (7-14 day response)  
**Step 2a:** If they share code → Fork, adapt for Mayo validation, publish improvements  
**Step 2b:** If no response → Implement from scratch using plan above  
**Step 3:** Publish to SAHVAI-Lab GitHub with proper attribution  

---

**Document Owner:** JT (SAHVAI Lab AI Assistant)  
**Created:** 2026-03-04  
**Status:** Proposal - Awaiting David's decision
