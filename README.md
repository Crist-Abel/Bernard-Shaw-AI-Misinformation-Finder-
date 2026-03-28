# BERNARD SHAW AI (Misinformation Finder) using Hybrid Deep Learning and Online Verification

The project focuses on detecting misinformation (or fake news) by combining a fine-tuned DistilBERT model with real-time online verification from trusted sources. The idea is not just to rely on machine learning for predicting news authenticity, but also to strengthen those predictions by cross-checking claims using live data from Wikipedia, GNews, and Google Fact Check APIs.

To achieve this, the system is structured to include offline training, testing, and evaluation of the model, ensuring that it performs reliably on unseen data. On top of that, a hybrid prediction logic is implemented, where the model’s output is supported and validated through external verification.

For practical usage, a Streamlit web interface is developed, allowing users to manually test news content and observe how the system analyzes and verifies it in real time.

## 1. Project Overview

Detecting misinformation is a challenging problem because AI models often fail with new or unseen news. To address this, the project uses a hybrid approach:

1. An offline trained DistilBERT model for fake/real classification.
2. Online verification of the user-entered news using:

   * Google Fact Check API
   * Wikipedia summary
   * GNews live articles

(Use your own API KEY)

The hybrid logic combines all three sources to produce a more reliable final verdict.

## 2. Dataset Used

The model is trained using the **WELFake Dataset**, which consists of both real and fake news articles.

* Total dataset size: 69,000+ records
* Label 1 = Fake, Label 0 = Real
* Includes title, text, and label

The dataset was split into training and testing using an 80:20 ratio.

## 3. Model Used

The project uses:

* DistilBERT (distilbert-base-uncased)
* Fine-tuned for binary classification
* Training was done for one epoch with AdamW optimizer and learning rate of 2e-5

The trained model is saved in `models/best_model/`.

## 4. Evaluation Results

The model was evaluated on 14,427 test samples.

**Results:**

* Accuracy: 99.87%
* Precision: 95.76%
* Recall: 99.13%
* F1-Score: 98.97%

**Confusion Matrix:**

|             | Predicted Real | Predicted Fake |
| ----------- | -------------- | -------------- |
| Actual Real | 7938           | 70             |
| Actual Fake | 57             | 7299           |

The model performs strongly on both classes with minimal false positives and false negatives.

---

## 5. Hybrid Verification System

Mistakes can still be made by offline models on new topics, thus, the project includes a hybrid verification stage.

For user-entered news:

1. The offline model predicts FAKE or REAL with confidence.
2. The system checks the claim online through:

   * Wikipedia API search
   * GNews API for recent news articles
   * Google Fact Check Tools API

Hybrid logic:

* If any fact-check source marks the claim as false → Final result is FAKE.
* If Wikipedia strongly matches the topic → Mark as TRUE.
* If live news articles support the claim → Mark as TRUE.
* If offline model says fake but no evidence online → Mark as UNCERTAIN.
* Otherwise, fallback to the AI prediction.

This hybrid approach significantly increases overall reliability.

## 6. Folder Structure

FakeNews-main/
│
├── data/
│   ├── train.csv
│   ├── WELFake_Dataset.csv
│   └── test.csv
│
├── models/
│   └── best_model/
│
├── utilities.py
├── preprocess.py
├── evaluate_model.py
├── local_test.py
├── test_api.py
├── online_sources.py
├── online_verify.py
├── hybrid_predict.py
├── train_distilbert.py
├── streamlit_app.py
├── make_test_split.py
├── dataset.py
└── fact_check.py

## 7. How to Run the Project

### Step 1: Create and activate a virtual environment

Windows:

python -m venv venv
.\venv\Scripts\activate

### Step 2: Install required libraries

pip install -r requirements.txt

### Step 3: Train the model (optional)

python train_distilbert.py

### Step 4: Evaluate the model

python make_test_split.py
python evaluate_model.py

### Step 5: Run the hybrid verification system

python online_verify.py

### Step 6: Run the Streamlit app

streamlit run streamlit_app.py

## 8. Features Implemented

* The text data was cleaned and preprocessed to make it suitable for training the model
* Information from different sources was brought together to form a more complete dataset
* Train/test splitting
* The DistilBERT model was then fine-tuned to classify news as either real or fake
* The model’s performance was analyzed using metrics such as accuracy, precision, recall, and F1-score
* Hybrid online verification using three APIs
* Streamlit interface for end-users
* Modular and clean code structure

## 9. Limitations

* The accuracy of the offline model largely depends on the quality and reliability of the dataset used.
* Sources like Wikipedia and GNews may occasionally return results that are not directly relevant to the query.
* Limitations in free API usage can restrict the number of online verification requests per day.
* The hybrid system is dependent on internet connectivity for real-time verification.

## 10. Future Improvements

* Replace DistilBERT with a stronger model like DeBERTa-v3.
* Add semantic similarity (sentence transformers) for better Wikipedia matching.
* Include more news APIs for better verification.
* Add better UI/UX for the Streamlit application.
* Deploy the system online.



