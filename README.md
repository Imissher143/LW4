# Laboratory Work 4 Activity 1 — Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

# DRIVE LINK
https://drive.google.com/drive/folders/1qWRfwrAkRGwY1DyItX0mTxAXM5JxtdGY?usp=drive_link
---

# Activity 1: Evaluation Metrics + Visualization

### Classification Report
<img width="591" height="554" alt="image" src="https://github.com/user-attachments/assets/078fac8b-2d2a-4373-ba93-72e7393dd615" />

**Description:**
A classification report showing the precision, recall, F1-score, and overall accuracy (0.61) of the LW3 baseline model across 20 herb classes.

---

### 2. Confusion Matrix
<img width="819" height="743" alt="image" src="https://github.com/user-attachments/assets/ec6375dc-c7bc-46e9-bb1f-81e86b44d0bd" />

**Description:**
A confusion matrix illustrating the prediction performance of the LW3 baseline model across 20 herb classes, highlighting correctly classified samples along the diagonal and misclassifications between visually similar classes.

---

### 3. (ROC) Curve and Area Under the Curve (AUC) Score
<img width="1061" height="734" alt="image" src="https://github.com/user-attachments/assets/47af0ec8-676f-4a48-a4de-e77a56ece94f" />


**Description:**
A ROC curve showing the classification performance of the LW3 baseline model across 20 herb classes, with an overall AUC of 0.9423, indicating strong class separability and high discriminative capability.

---

### 4. Precision, Recall, F1-score per Class
<img width="1056" height="408" alt="image" src="https://github.com/user-attachments/assets/e9e5a0e6-9449-4c0f-adcb-93edaf7da6e4" />

**Description:**
A grouped bar chart comparing precision, recall, and F1-score for each class, allowing quick identification of performance imbalances—highlighting strong classes like lemon_basil and miyana, while revealing weaker ones such as sambang_getih and jeruk_besar where all three metrics lag noticeably.

---

# Activity 2: Model Interpretability using Gradient-weighted Class Activation Mapping (Grad-CAM) - Visualizing CNN Decisions Using Grad-CAM for Explainable Image Classification


### 5. Grad-CAM Heatmap
<img width="353" height="351" alt="image" src="https://github.com/user-attachments/assets/4dfb8bb8-7ea8-41a0-8a4a-9ce4ac9699c0" />

**Description:**
This raw heatmap identifies the specific regions in the image that had the highest impact on the model's final classification decision. Bright yellow/green areas indicate high-influence features.

---

### 6. Grad-CAM Overlay
<img width="334" height="352" alt="image" src="https://github.com/user-attachments/assets/58170292-3c76-4599-a7ea-7c95393c6ead" />

**Description:**
By superimposing the heatmap onto the original image, we can see exactly what the model "looked at." for example, the model is highlighting various leaf textures and serrated edges.

---
### Grad-CAM Interpretation 

**Description:**
The Grad-CAM results show a scattered heatmap that is beginning to focus on the correct object. While the baseline model correctly ignored the background, its "attention" was fragmented across various leaf edges, suggesting it was relying on general "greenery" rather than specific herb structures (Weak Feature Learning). However, because the primary "hot zones" are located directly on the leaf textures, there is clear evidence that the model is looking at the plant to make decisions; the architectural improvements in Activity 3 are simply needed to consolidate these scattered highlights into a single, confident detection of the herb's unique features.

---

# Activity 3: Model Enhancement and Performance Optimization


### 7. Train Improved Model (30 epochs)
<img width="1072" height="771" alt="image" src="https://github.com/user-attachments/assets/966615e0-4b6b-4c36-916e-d0a5c3eff1b0" />
<img width="1064" height="313" alt="image" src="https://github.com/user-attachments/assets/628e95ae-acc8-49c5-a9c1-9dfcda21b4b0" />

**Description:**
Shows the training logs where Batch Normalization and Dropout were applied. The steady decrease in loss and rise in accuracy indicates a more stable and efficient learning process compared to the baseline.

---

### 8. Improved Classification Report
<img width="513" height="467" alt="image" src="https://github.com/user-attachments/assets/1efac6b8-a655-4502-b894-fe6cd56a79bb" />
**Description:**
A detailed classification report summarizing precision, recall, and F1-score for each class, offering a clear numerical breakdown of model performance—showing consistently strong results for classes like mayana, sambong, and lemon_basil, while exposing weaker classifications such as sambang_getih and ginger, which have noticeably lower F1-scores and recall.

---

### 9. Improved Confusion Matrix
<img width="823" height="747" alt="image" src="https://github.com/user-attachments/assets/4897af63-085c-470e-ba41-703467eb6c7d" />

**Description:**
Displays a much cleaner diagonal line, meaning more herbs are correctly classified. It specifically shows that previous "blind spots" for certain herbs have been largely resolved.

---

### 10. Improved (ROC) Curve and Area Under the Curve (AUC) Score
<img width="1059" height="724" alt="image" src="https://github.com/user-attachments/assets/88717431-51fd-4000-b885-09dd6ad7f7e7" />


**Description:**
Each class curve is pushed further toward the top-left, with many reaching an AUC of 1.00. This confirms the model has an excellent ability to distinguish between the 20 herb types.

---

### 11. Improved Precision, Recall, F1-score per Class
<img width="1064" height="408" alt="image" src="https://github.com/user-attachments/assets/9f5b5ef2-f50f-473c-8b7f-79c05a1c78af" />


**Description:**
A bar chart showing balanced performance across all metrics. Unlike the baseline, every herb now has a functional score, proving the model no longer "ignores" harder-to-learn classes.

---

### Compare Results (Before vs After)
<img width="584" height="277" alt="image" src="https://github.com/user-attachments/assets/13076f65-b559-4774-93ef-4ec8365078ac" />

**Description:**
A comparison highlighting the 66.20% accuracy boost and improved F1-scores. It confirms that the architectural enhancements successfully closed the gap between training and validation performance.


---

# 📋 Guide Questions — LW4: Improving CNN Performance

---

## A. Model Evaluation Analysis

**1. What were the weakest-performing classes based on the confusion matrix?**
The confusion matrix from the LW3 baseline reveals the weakest classes as those with low diagonal values and many misclassifications spread across other columns. These are classes that visually look similar to each other, causing the baseline model to frequently mix them up.

**2. How did Precision, Recall, and F1-score vary across classes?**
Based on the per-class bar chart, visually distinct classes scored high across all three metrics, while similar-looking classes showed lower recall since the baseline model kept confusing them with nearby classes.

**3. What does a low recall indicate in your model?**
It means the model is "missing" that class — it sees the image but labels it as something else instead. For example, a class with 0.40 recall means the model only got 40% of those images right.

**4. How does AUC score reflect model performance compared to accuracy?**
AUC shows how well the model separates each class across all thresholds, not just one cutoff. A model can have decent AUC but still low accuracy if some classes dominate the dataset.

---

## B. Model Improvement

**5. How did data augmentation affect validation accuracy?**
The LW4 model adds `RandomBrightness` on top of flip, rotation, zoom, and contrast — forcing the model to recognize classes regardless of lighting or angle, which directly improved generalization to the validation set.

**6. Why is Batch Normalization important in CNNs?**
Every Conv2D block uses `BatchNormalization()` right after each convolution. It stabilized training and prevented loss spikes, letting the model learn smoothly across all 5 blocks.

**7. What role did Dropout play in improving your model?**
Dropout increases progressively from 0.1 in Block 1 up to 0.3 in the head, preventing the model from memorizing specific patterns. It forced the network to learn general features rather than relying on specific neurons.

**8. How did Early Stopping prevent overfitting?**
`EarlyStopping(patience=7, restore_best_weights=True)` automatically stops training when val_accuracy stops improving and snaps back to the best weights — so the saved model never gets a chance to overfit.

---

## C. Performance Comparison

**9. What improvements were observed after modifying the model?**
The comparison table shows LW4 achieving higher val accuracy, better F1-score, and improved AUC over the LW3 baseline. The generalization gap is also flagged as ✅ Good Fit when train - val ≤ 5%.

**10. Which enhancement contributed the most to performance improvement? Why?**
The new Block 5 (512 filters) combined with Cosine Decay LR contributed the most — Block 5 gave the model enough depth to learn complex features, while cosine decay squeezed out the best accuracy within just 30 epochs.

**11. Did the gap between training and validation accuracy decrease? Explain.**
Yes, because LW4 uses lower L2 (5e-5), moderate dropout, and stronger augmentation — all balanced so the model learns well without memorizing. The gap is directly computed and labeled as Good Fit, Slight Overfit, or Overfitting.

---

## D. Explainability (Grad-CAM Integration)

**12. How did Grad-CAM help in understanding model predictions?**
The `show_gradcam_fixed()` function builds a sub-model targeting `last_conv` and generates a heatmap showing which regions drove the prediction. It makes the model's decision visible instead of being a black box.

**13. Did the improved model focus on more relevant regions? Provide evidence.**
With 5 conv blocks up to 512 filters, LW4 learns more detailed features — the Grad-CAM overlay shows a more concentrated heatmap on the actual subject of the image rather than scattered across the background.

**14. Why is explainability important in real-world AI applications?**
Users need proof that the model is identifying things for the right reasons, not because of background noise or shadows. Without Grad-CAM, you'd have no way to catch a model that's "cheating" its way to high accuracy.
