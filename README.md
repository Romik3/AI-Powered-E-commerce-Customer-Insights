# AI-Powered E-commerce Customer Insights Dashboard

## 📖 Introduction

In the world of e-commerce, customer feedback is gold, but manually analyzing thousands of reviews is an impossible task. This project automates this process by building an end-to-end data pipeline that transforms raw, unstructured customer reviews into an interactive "Action Dashboard" designed for a product manager. The goal is to move beyond simple reporting and provide a tool that helps answer the question: **"What is the most important problem I should be solving right now?"**

---

## ✨ Key Features

*   **Definitive Sentiment Analysis:** A robust hybrid model that uses user ratings, recommendation status, and VADER text analysis for highly accurate sentiment classification.
*   **Automated Problem Identification:** A Hugging Face Transformer model automatically classifies negative reviews into clear business categories (e.g., "Sizing/Fit," "Fabric/Quality").
*   **High-Performance Inference:** The classification pipeline is optimized for GPUs using half-precision (`fp16`) and batching for maximum speed.
*   **Interactive "Action Dashboard":** Built in Power BI, it features a unique problem matrix to pinpoint problem areas, a "Problem Products" list to identify specific SKUs, and a "Voice of the Customer" feed for deep qualitative insights.

---

## 🛠️ Tech Stack

*   **Data Analysis & NLP:** Python, Pandas, NLTK, Scikit-learn (`LatentDirichletAllocation`)
*   **AI & Machine Learning:** Hugging Face `transformers`, PyTorch (for GPU inference)
*   **Data Visualization:** Power BI
*   **Environment:** Google Colab (Jupyter Notebooks)

---

## 🔬 The Data Science Workflow

This project followed a rigorous, iterative data science process:

1.  **Data Cleaning & Preprocessing:** The initial dataset of 23,000+ reviews was cleaned, and the text was preprocessed using standard NLP techniques like lowercasing, stop-word removal, and lemmatization (NLTK).

2.  **The Evolution of Sentiment Analysis:**
    *   **Attempt 1 (VADER):** Initially used a purely text-based model but found it was easily fooled by sarcastic or mixed-signal reviews.
    *   **Attempt 2 (Rating-Based):** Switched to a model based only on star ratings. This was more accurate but missed the nuance in 3-star reviews.
    *   **Final Model (Definitive Hybrid):** The final model uses a hierarchy of trust: it prioritizes the user's explicit `Rating` and `Recommended IND` status and only uses the VADER text score to resolve ambiguity in 3-star reviews. This provided the most accurate and defensible sentiment classification.

3.  **Topic Modeling:** Used Latent Dirichlet Allocation (LDA) to identify the broad, underlying topics discussed across all reviews, providing a high-level overview of customer conversations.

4.  **Negative Review Classification:** To get specific, actionable insights, a zero-shot classification model from Hugging Face was used to categorize the *correct* set of negative reviews. This removed the need for a slow, rate-limited external API and demonstrated modern, in-notebook AI capabilities.

---

## 🚀 How to Run

1.  Clone this repository: `git clone [your_repo_link]`
2.  Install the required packages: `pip install -r requirements.txt`
3.  Launch the Jupyter Notebook: `jupyter notebook "Project Notebook.ipynb"`
4.  Run the cells sequentially to process the data and generate the final `Product_Review_Analysis_Final.csv`.
5.  Open the `.pbix` file in Power BI Desktop to explore the interactive dashboard.
