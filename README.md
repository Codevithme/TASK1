# CODSOFT
# Spam Message Classification using Machine Learning

## Overview

This project builds a **machine learning model to detect spam messages**. The system analyzes the text of an SMS message and determines whether it is **spam (unwanted promotional message)** or **ham (normal message)**.

The project uses **Natural Language Processing (NLP)** techniques to convert text into numerical features and then trains a classification model to identify patterns commonly found in spam messages.

---

## Objective

The goal of this project is to design a model that can automatically classify SMS messages into two categories:

* **Spam (1)** – unwanted promotional or fraudulent messages
* **Ham (0)** – normal or legitimate messages

This type of system is widely used in **email filtering, SMS filtering, and messaging platforms** to protect users from spam.

---

## Technologies Used

The project is implemented using the following tools and libraries:

* **Python** – programming language used for development
* **Pandas** – used for loading and managing the dataset
* **Regular Expressions (re)** – used for text cleaning
* **Scikit-learn** – machine learning library used for model training and evaluation
* **TF-IDF Vectorizer** – converts text messages into numerical vectors
* **Logistic Regression** – classification algorithm used for prediction
* **Matplotlib** – used for optional visualization

---

## Dataset

The dataset used in this project contains SMS messages labeled as spam or ham.

### Dataset Columns

| Column | Description                 |
| ------ | --------------------------- |
| v1     | Message label (ham or spam) |
| v2     | SMS message text            |

During preprocessing, these columns are renamed to:

| Column  | Description                          |
| ------- | ------------------------------------ |
| label   | Message category (0 = ham, 1 = spam) |
| message | SMS text                             |

---

## Project Workflow

### 1. Data Loading

The dataset is loaded from a CSV file using Pandas. Only the required columns containing the message and label are selected.

---

### 2. Data Preprocessing

Text preprocessing improves the quality of the data before training the model.

The following steps are applied:

* Convert text to lowercase
* Remove numbers and special characters
* Keep only alphabetic characters

This helps the model focus on meaningful words.

---

### 3. Feature Extraction

The cleaned text messages are converted into numerical vectors using **TF-IDF (Term Frequency–Inverse Document Frequency)**.

Additional settings used:

* **Stop word removal** to remove common words
* **Bigrams (1,2)** to capture word combinations
* **max_df = 0.95** to remove extremely frequent words

---

### 4. Data Splitting

The dataset is divided into two parts:

* **Training Data (80%)** – used to train the model
* **Testing Data (20%)** – used to evaluate performance

---

### 5. Model Training

A **Logistic Regression classifier** is trained using the TF-IDF features.

The model uses:

* **Balanced class weights** to handle uneven distribution between spam and ham messages
* **Maximum iterations set to 1000** to ensure convergence during training

---

### 6. Spam Detection Threshold

Instead of using the default classification threshold (0.5), a **lower threshold (0.35)** is used.

This adjustment helps the model detect more spam messages by increasing sensitivity to spam probabilities.

---

### 7. Model Evaluation

The model performance is measured using:

* **Accuracy Score** – overall correctness of predictions
* **Confusion Matrix** – shows correct and incorrect classifications
* **Classification Report** – provides precision, recall, and F1-score

These metrics help understand how well the model detects spam messages.

---

## Installation

Install the required Python libraries using pip:

```
pip install pandas scikit-learn matplotlib
```

---

## Running the Project

1. Place the dataset file **spam.csv** in the project folder.

2. Run the Python script:

```
python spam_classifier.py
```

3. The program will train the model and display evaluation results including accuracy and classification metrics.

---

## Project Structure

```
spam_classification_project
│
├── spam.csv
├── spam_classifier.py
└── README.md
```

---

## Possible Improvements

This project can be enhanced in several ways:

* Apply advanced text preprocessing such as stemming or lemmatization
* Compare multiple machine learning algorithms like Naive Bayes, Support Vector Machines, or Random Forest
* Use deep learning models such as LSTM or BERT for improved performance
* Build a real-time spam detection web application using Flask or Streamlit

---

## Conclusion

This project demonstrates how machine learning and natural language processing can be used to automatically identify spam messages. By converting text data into numerical features and training a classification model, the system can effectively distinguish between legitimate messages and spam.

Such techniques are widely used in modern communication platforms to improve user experience and reduce unwanted messages.

