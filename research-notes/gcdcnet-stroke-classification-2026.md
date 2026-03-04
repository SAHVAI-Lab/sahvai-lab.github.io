# GCDCNet: Attention-Enhanced Deep Learning for Stroke Classification

**Added to SAHVAI Collection:** 2026-03-04  
**Source:** Morning Pulse Research Alert  
**Priority:** ⭐ High (directly applicable to AI/imaging initiatives)

---

## Citation

**Che S, Che S, Liu X, Du P, Wang Z, Chen Y, Hu Y, Kong L**  
*Attention-enhanced deep learning model for automated classification of hemorrhagic and ischemic stroke on CT imaging.*  
Eur J Med Res. 2026 Mar 3. doi: 10.1186/s40001-025-03784-w

[PubMed](https://pubmed.ncbi.nlm.nih.gov/41776569/) | [DOI](https://doi.org/10.1186/s40001-025-03784-w)

---

## Abstract Summary

### Background
Hemorrhagic and ischemic strokes require completely different treatment plans, making rapid and accurate classification crucial for clinical decision-making. This study proposed **GCDCNet**, a lightweight and efficient deep learning model for intelligent stroke CT classification.

### Methods
- **Dataset:** Public stroke CT dataset
  - 964 hemorrhagic strokes
  - 1,551 ischemic strokes
- **Architecture:** Based on GhostNet lightweight framework
- **Key Components:**
  - SCSE (Spatial & Channel Squeeze-Excitation) attention mechanism
  - Dilated convolution
  - Channel shuffling for feature optimization
- **Training:** Cross-entropy loss + Adam optimizer
- **Validation:** Grad-CAM visualization analysis

### Results
**Performance Metrics (Test Set):**
| Metric | Score |
|--------|-------|
| Accuracy | 99.26% |
| Recall | 99.33% |
| F1 Score | 99.13% |
| Precision | 98.94% |
| AUC-ROC | 0.9996 |
| Parameters | 2.7M (lightweight!) |

**Comparison:** Outperformed ConvNeXt, EfficientNet, GhostNet, HRNet, and ViT.

**Interpretability:** Grad-CAM visualization showed model discrimination areas were highly consistent with clinician focus areas.

### Conclusion
GCDCNet demonstrates superior accuracy, lightweight design, and good generalization for stroke CT classification. Suitable for:
- Early stroke screening
- Emergency triage
- Telemedicine applications
- Medical resource optimization

---

## Technical Architecture: GCDCNet

### Core Components

1. **GhostNet Backbone**
   - Lightweight architecture (2.7M parameters vs. 20-80M for competitors)
   - Efficient feature extraction

2. **SCSE Attention Mechanism**
   - Spatial attention: Focuses on *where* lesions are located
   - Channel attention: Focuses on *which* features matter
   - Combined squeeze-and-excitation enhances lesion area focus

3. **Dilated Convolution**
   - Expands receptive field without increasing parameters
   - Captures multi-scale contextual information

4. **Channel Shuffling**
   - Enables information exchange between feature channels
   - Improves feature fusion

### Why It Works
The attention mechanism guides the model to focus on clinically relevant regions (hemorrhage/ischemia) rather than scanning the entire image uniformly. This mimics how radiologists visually search for abnormalities.

---

## Relevance to SAHVAI Lab

### Direct Applications

1. **Attention Mechanisms for SAH Volume Estimation**
   - SCSE attention could improve SAHVAI-3D/4D focus on hemorrhage regions
   - Reduce false positives from CSF/contrast artifacts

2. **Lightweight Deployment**
   - 2.7M parameters = edge deployment feasible (bedside, ambulances)
   - Real-time inference on standard GPUs

3. **Interpretability via Grad-CAM**
   - Critical for clinical validation
   - Helps clinicians trust AI decisions
   - Aligns with eSAH score validation methodology

4. **Emergency Triage**
   - Fast hemorrhagic vs. ischemic classification
   - Could complement SAHVAI for SAH subtyping (aneurysmal vs. non-aneurysmal)

### Integration Ideas

**Short-term:**
- Benchmark SCSE attention module against current SAHVAI architecture
- Test Grad-CAM visualization on SAHVAI-3D hemorrhage detection

**Medium-term:**
- Hybrid model: GCDCNet triage → SAHVAI volumetrics → eSAH scoring
- Multi-task learning: Classify stroke type + estimate SAH volume simultaneously

**Long-term:**
- Federated learning across Mayo sites using lightweight GCDCNet backbone
- Mobile/edge deployment for telemedicine stroke screening

---

## Key Takeaways for Mayo AI/Imaging Initiatives

✅ **Lightweight matters:** 2.7M parameters vs. 20-80M competitors = deployable at point-of-care  
✅ **Attention works:** SCSE mechanism achieved near-perfect discrimination (AUC 0.9996)  
✅ **Interpretability is essential:** Grad-CAM alignment with clinician focus = clinical trust  
✅ **Public datasets enable innovation:** 2,515 images sufficient for 99%+ accuracy  

---

## Questions for Further Investigation

1. **Generalization:** How does GCDCNet perform on Mayo's internal stroke CT datasets?
2. **SAH Subtyping:** Can attention mechanisms distinguish aneurysmal vs. non-aneurysmal SAH?
3. **Multi-modality:** Would SCSE attention improve MRI-based stroke classification?
4. **Real-time Inference:** Latency benchmarks on clinical workstations?
5. **Federated Learning:** Privacy-preserving training across multiple Mayo sites?

---

## Action Items

- [ ] Share with SAHVAI Lab team (Sharma, Salman, Wei, etc.)
- [ ] Request Mayo IRB for internal validation study
- [ ] Contact authors (Kong L - klb1984@163.com) for architecture details
- [ ] Benchmark on Mayo stroke CT dataset
- [ ] Test SCSE attention module integration with SAHVAI-3D

---

## Funding Acknowledgment

"Registry Study on Naoxueshu Oral Liquid for Prevention and Treatment of Intracerebral Hemorrhage" - China Association of Chinese Medicine (CACM) Grant No. 2021XS-001-04

---

**Document Status:** Draft research note  
**Next Review:** 2026-03-11 (lab meeting)  
**Owner:** W. David Freeman, MD / SAHVAI Lab
