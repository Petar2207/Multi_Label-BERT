# 📘 Survey Response Classification — Multi-Label BERT Model

This project builds a **multi-label text classification model** for survey responses using a fine-tuned **multilingual BERT** model. Each prediction assigns one or more categories based on the combined text of the **questionText** and **answer** fields.

The project includes the complete workflow: data preprocessing, label binarization, tokenization, selective BERT layer unfreezing, model training, threshold optimization, model export, and an inference pipeline.

---

## 🚀 Features

### **Multi-Label Classification**

### **Multilingual BERT Fine-Tuning**
Uses **`bert-base-multilingual-cased`**, enabling support for multiple languages.

### **Selective Layer Freezing**
- All lower transformer layers are frozen  
- Only the top **4 BERT layers** and the **classification head** are trainable  
This stabilizes training and prevents overfitting.

### **Threshold Optimization**
Optimal decision thresholds are computed per label to maximize **F1-score**.

### **Full Model Export**
The final model export includes:
- Model weights  
- Tokenizer  
- Label list  
- Optimized thresholds  
- Training arguments  
- Checkpoints  

---


## 📦 Data Preparation

Performed in the training notebook:

- Text cleaning and whitespace normalization  
- Removal of missing or empty rows  
- Extraction of category strings into label lists  
- Multi-hot encoding via **MultiLabelBinarizer**  
- Two-stage splitting into **train / validation / test** sets
- Upsampling

---

## 🔤 Tokenization

- Inputs created by concatenating:  
  **`questionText + answer`**  
- Uses standard BERT tokenization with:  
  - truncation  
  - padding  
  - attention masks  

---

## 🤖 Model Architecture

The system uses **`AutoModelForSequenceClassification`** configured for multi-label classification.

- Loss function: **BCEWithLogitsLoss**  
- Fully compatible with multi-label outputs  

---

## 🔒 Layer Freezing Strategy

During training:

- All BERT layers start **frozen**
- Then, **only the top 4 encoder layers** and the **classification head** are unfrozen
- Remaining layers stay frozen throughout training  
This improves efficiency and performance, especially on smaller datasets.

---

## 🏋️ Training

Training is powered by the HuggingFace **Trainer API**, including:

- Evaluation every epoch  
- Metrics: precision, recall, micro/macro F1  
- Automatic best-checkpoint saving  
- Full logging and monitoring support  

---

## 📈 Threshold Optimization

After training:

- Model predicts raw logits on the validation set  
- Label-specific thresholds are computed to maximize F1  
- These thresholds significantly improve multi-label prediction accuracy  

---

## 💾 Model Saving

The model export includes:

- Trained model  
- Tokenizer  
- Label names  
- Best-performing thresholds  
- Training arguments  
- Checkpoints  
- A downloadable ZIP file with everything included  

---

## 🔍 Inference

The inference notebook loads:

- Final trained model  
- Tokenizer  
- Label names  
- Saved per-label thresholds  

It then processes new **question + answer** pairs and outputs all predicted categories.

---

## 📜 License

This project is licensed under the **MIT License**.

---

## 👤 Author

**Petar Rajic**

