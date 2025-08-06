# Survey Classification Model: Multi-Label Classification with BERT

This project aims to build a **multi-label classification model** for survey responses, where the goal is to predict multiple categories based on the survey's **questionText** and **answer**. Using **BERT** (Bidirectional Encoder Representations from Transformers) from the Hugging Face library, we fine-tune the model to identify which survey responses belong to which labels.

🎯 **Project Goal**
- **Primary Objective**: 
  To classify survey responses into multiple categories using a BERT-based model. The focus is on predicting categories (multi-label classification) for each pair of **questionText** and **answer**.

✅ **Workflow Summary**

1. **Data Cleaning & Preparation**
   - Removed irrelevant column (e.g., `category_type`) from the dataset.
   - Split the data into features (`questionText`, `answer`) and labels (`category_type`).
   - Performed tokenization of text using BERT tokenizer for model input.
   - Data was split into a training set (90%) and test set (10%) for evaluation.
   - **Automated Preprocessing Added**: The script includes a preprocessing pipeline to tokenize text data and prepare it for model training.

2. **Model Building**
   - Used the **BERT-base-multilingual-cased** model to fine-tune for multi-label classification.
   - Implemented a custom **Trainer class** to use **BCEWithLogitsLoss** for multi-label classification tasks.
   - Evaluated model performance with custom metrics such as **F1 score**, **Precision**, and **Recall**.

3. **Training & Evaluation**
   - Model was trained using 3 epochs with batch sizes of 8.
   - Evaluated the model during training and after the final epoch to determine optimal thresholds for label classification.
   - Saved the trained model and tokenizer for future use, along with **best thresholds** and **training arguments**.
4. **Saving & Downloading the Model**
   - After training, the model and tokenizer were saved in a directory for easy retrieval.
   - Created a zip file of the saved model and training artifacts, allowing the user to download and use it for inference or further training.
   - 
**Model Loading and Example Usage**
I also loaded notebook that demonstrates how to load a pre-trained model and provides an example of how to use it for predictions.

🛠️ **Tech Stack**
- **Languages**: Python
- **Libraries**: pandas, numpy, scikit-learn, torch, transformers, matplotlib, seaborn

📜 **License**
This project is licensed under the MIT License — free to use and modify.

👤 **Author**
Petar Rajic

---

To install the required libraries, use:

```bash
pip install --upgrade --force-reinstall transformers==4.52.4
pip install -q transformers datasets scikit-learn pandas accelerate openpyxl
