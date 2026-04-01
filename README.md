# Laboratory Work 4 Activity 1 — Improving CNN Performance Using Regularization, Fine-Tuning, and Advanced Evaluation

# DRIVE LINK
https://drive.google.com/drive/folders/1qWRfwrAkRGwY1DyItX0mTxAXM5JxtdGY?usp=drive_link
---

# Activity 1: Evaluation Metrics + Visualization

### Classification Report
<img width="448" height="424" alt="image" src="https://github.com/user-attachments/assets/88d77fae-8ff8-42ae-96ca-319a88d872eb" />

**Descrition:**
A detailed summary providing the precision, recall, and F1-score for each of the 20 herb classes, along with the overall model accuracy of 0.60.
---

### 2. Confusion Matrix
<img width="768" height="678" alt="image" src="https://github.com/user-attachments/assets/58487756-fbee-4dd6-b761-f191b03fb3c8" />

**Descrition:**
A visual grid showing the frequency of correct and incorrect predictions for each class, highlighting specific areas where the model confuses similar herbs.

---

### 3. (ROC) Curve and Area Under the Curve (AUC) Score
<img width="733" height="604" alt="image" src="https://github.com/user-attachments/assets/551fe746-3ced-452e-80ce-b7e71d954d9b" />

**Descrition:**
A plot illustrating the model's diagnostic ability across various thresholds, with an Area Under the Curve (AUC) score for each class indicating how well the model distinguishes between them.

---

### 4. Precision, Recall, F1-score per Class
<img width="1003" height="503" alt="image" src="https://github.com/user-attachments/assets/6dec6bf0-5c5d-45a7-9c33-40e4868eccf3" />

**Descrition:**
A bar chart providing a side-by-side visual comparison of key performance metrics across all classes, making it easy to identify weakest-performing classes like sambang_getih.

---

# Activity 2: Model Interpretability using Gradient-weighted Class Activation Mapping (Grad-CAM) - Visualizing CNN Decisions Using Grad-CAM for Explainable Image Classification


### 5. Grad-CAM Heatmap
<img width="353" height="351" alt="image" src="https://github.com/user-attachments/assets/4dfb8bb8-7ea8-41a0-8a4a-9ce4ac9699c0" />



---

### 6. Grad-CAM Overlay
<img width="334" height="352" alt="image" src="https://github.com/user-attachments/assets/58170292-3c76-4599-a7ea-7c95393c6ead" />



---
### Grad-CAM Interpretation 

The Grad-CAM results show a scattered heatmap that is beginning to focus on the correct object. While the baseline model correctly ignored the background, its "attention" was fragmented across various leaf edges, suggesting it was relying on general "greenery" rather than specific herb structures (Weak Feature Learning). However, because the primary "hot zones" are located directly on the leaf textures, there is clear evidence that the model is looking at the plant to make decisions; the architectural improvements in Activity 3 are simply needed to consolidate these scattered highlights into a single, confident detection of the herb's unique features.

---

# Activity 3: Model Enhancement and Performance Optimization


### 8. Train Improved Model (20 epochs)
<img width="769" height="589" alt="image" src="https://github.com/user-attachments/assets/508e4d85-4ca8-41a3-816c-bab99ed1c7c9" />


---

### 9. Improved Classification Report
<img width="411" height="425" alt="image" src="https://github.com/user-attachments/assets/d982433e-f970-47e8-8f49-40c4c4327f1d" />



---

### 10. Improved Confusion Matrix
<img width="763" height="673" alt="image" src="https://github.com/user-attachments/assets/b2622a98-b3d0-4f2d-803d-c5b96083e1e6" />


---

### 11. Improved (ROC) Curve and Area Under the Curve (AUC) Score
<img width="719" height="593" alt="image" src="https://github.com/user-attachments/assets/f3023d15-b221-453b-9e4c-c121f7686c3a" />


---

### 12. Improved Precision, Recall, F1-score per Class
<img width="1007" height="503" alt="image" src="https://github.com/user-attachments/assets/b27084ad-f921-4307-99ba-01d11316d6e9" />


---

### Compare Results (Before vs After)
<img width="333" height="150" alt="image" src="https://github.com/user-attachments/assets/7b49693b-dd5a-40c7-983a-ebeb649e02f2" />

---

### 13. Visualization of Improvement
<img width="835" height="395" alt="image" src="https://github.com/user-attachments/assets/2f2c0dce-308f-4fa3-a41b-2a2df57384c4" />


---

## 14. GUIDE QUESTIONS
**A. Model Evaluation Analysis**
1. What were the weakest-performing classes based on the confusion matrix? sambang_getih was the baseline's worst (0.04 recall). Now, the main challenges are niyog_niyugan and lemon_balm due to their similarity to other leafy herbs.
2. How did Precision, Recall, and F1-score vary across classes? Herbs with unique shapes have high precision. "Cousin" plants (similar looking) have lower recall because the model occasionally confuses them.
3. What does a low recall indicate in your model? This indicates the model is "missing" the plant—e.g., it sees a bay_laurel but incorrectly labels it as something else.
4. How does AUC score reflect model performance compared to accuracy? A high AUC (0.90+) shows the model "understands" the differences between classes well, even while the raw accuracy (66%) is still catching up.

**B. Model Improvement**
5. How did data augmentation affect validation accuracy? Forced the model to learn shapes regardless of angle or zoom, leading to a 6% accuracy boost.
6. Why is Batch Normalization important in CNNs? Stabilized the training process and prevented volatile "spikes" in the loss curves.
7. What role did Dropout play in improving your model? Prevented the model from being "lazy" by relying on specific pixels; it forced the network to learn robust, overall patterns.
8. How did Early Stopping prevent overfitting? Automatically stopped training at Epoch 20 to prevent overfitting (memorizing the training photos).
 
**C. Performance Comparison**
9. What improvements were observed after modifying the model? Fixed the "zero-score" classes. Every herb in the dataset now has a functional F1-score.
10. Which enhancement contributed the most to performance improvement? Why? Augmentation + Dropout. These effectively closed the gap between "memorizing" and "actually understanding."
11. Did the gap between training and validation accuracy decrease? Explain. The gap between training and validation narrowed (56% vs 66%), indicating the model generalizes much better to new data.

**D. Explainability (Grad-CAM Integration)**
12. How did Grad-CAM help in understanding model predictions? Grad-CAM proved the model is focusing on leaf textures and patterns rather than irrelevant background noise like soil or pots.
13. Did the improved model focus on more relevant regions? Provide evidence. Improved heatmaps are more concentrated on the center of the leaves rather than scattered along random edges.
14. Why is explainability important in real-world AI applications? Explainability is key for real-world use. Users need to see that the AI is identifying the plant based on its actual features, not a shadow or a background color.

---

