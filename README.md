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
## Guide Questions & Answers

### A. Model Evaluation Analysis

#### 1. What were the weakest-performing classes based on the confusion matrix?
The weakest class was `sambang_getih`, which got a super low F1-score of only 3%. Other struggling classes were `ginger` and `bay_laurel`, which both scored below 40%.

#### 2. How did Precision, Recall, and F1-score vary across classes?
The scores varied heavily because some plant types were much easier for the network to recognize. For example, `lemon_basil` reached a high F1-score of 86%, while `sambang_getih` dropped close to zero.

#### 3. What does a low recall indicate in your model?
A low recall means the model is completely missing a lot of the actual target images during testing. Instead of finding them, it mistakenly labels them as other classes.

#### 4. How does AUC score reflect model performance compared to accuracy?
Even though the baseline overall accuracy was low at 61%, the AUC score was very high at 0.9423. This shows the model still has great potential to separate the classes once training issues are fixed.

---

### B. Model Improvement

#### 5. How did data augmentation affect validation accuracy?
Data augmentation helped by forcing the model to look at random flipped and rotated images instead of memorizing them. This fixed the overfitting problem and let the validation accuracy smoothly rise to 74.8%.

#### 6. Why is Batch Normalization important in CNNs?
Batch Normalization scales the data outputs inside the network layers so they stay stable during training. This makes the model learn much faster and prevents gradients from blowing up.

#### 7. What role did Dropout play in improving your model?
Dropout randomly deactivated a percentage of neurons during training so the network wouldn't rely on fixed paths. This stopped the model from over-memorizing the training dataset.

#### 8. How did Early Stopping prevent overfitting?
Early stopping watched the validation loss and automatically shut down training when it stopped improving. This kept the model from running too long and saved the best weights.

---

### C. Performance Comparison

#### 9. What improvements were observed after modifying the model?
The validation accuracy jumped from 61% in the baseline up to 74.8% in the improved model. The overall training curves also looked much smoother and the final loss dropped down significantly.

#### 10. Which enhancement contributed the most to performance improvement? Why?
Adding Batch Normalization and Dropout together contributed the most to the improvement. They directly targeted and fixed the baseline's main issue by stabilizing the layers and stopping severe overfitting.

#### 11. Did the gap between training and validation accuracy decrease? Explain.
Yes, the gap closed up tightly because the regularization layers forced the model to generalize better. The final validation accuracy (74.8%) ended up staying very close to the training accuracy (75.1%).that the model is identifying things for the right reasons, not because of background noise or shadows. Without Grad-CAM, you'd have no way to catch a model that's "cheating" its way to high accuracy.
