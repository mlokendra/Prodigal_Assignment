

# 📊 Call Sentiment Analysis

This project analyzes call transcripts between agents and borrowers in a consumer finance setting.
The goal is to generate **overall agent and borrower sentiment scores** per call and evaluate whether these scores are predictive of call dispositions (positive/negative outcomes).

---

## 📂 Project Structure

```
├── call_metadata.csv              # Metadata with call_id, duration, disposition, type
├── conversations/                 # Folder of .txt transcripts (one file per call_id)
├── call_sentiment_scores.csv      # Output: agent & borrower sentiment scores
├── notebooks/
│   ├── Prodigal_Assignment.ipynb  # Sentiment scoring pipeline
├── requirements.txt               # Python dependencies
├── README.md                      # Instructions 
├── Summary Document.pdf           # A short document answering the Assignment Questions
```

---

## ⚙️ Setup

### 1. Clone the repo & move into it

```bash
git clone https://github.com/mlokendra/Prodigal_Assignment
cd Prodigal_Assignment
```

### 2. Create a virtual environment (optional but recommended)

```bash
python3 -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Pipeline

### Sentiment Scoring

Run the main script to process all transcripts and generate call-level sentiment scores:

```bash
python full_sentiment_pipeline.py
```

This will output a CSV:

```
call_id,agent_sentiment,borrower_sentiment,disposition,type
...
```

### Jupyter Notebooks

Open the notebooks for interactive exploration:

```bash
jupyter notebook
```

---

## 📈 Evaluation Results

* **Borrower sentiment** is predictive of call disposition; agent sentiment is not that much.
* **Logistic regression feature importances**:

  * Agent sentiment: **0.15**
  * Borrower sentiment: **0.85**
* **Performance (n=2000 calls):**

  * Accuracy: **0.6225**
  * ROC AUC: **0.6653**
  * F1 Score: **0.627**
* **Correlation with outcomes:**

  * Agent: **r = 0.042, p = 0.0576** (not significant)
  * Borrower: **r = 0.254, p ≈ 9.66e-31** (significant)

---

## 🔮 Next Steps

* Replace **TextBlob** with **transformer-based sentiment models** (e.g., FinBERT, RoBERTa).
* Add **sentiment trajectory features** and **interaction terms** (e.g., agent–borrower sentiment gap).
* Validate on a **larger dataset** and compare with **human-labeled sentiment annotations**.


