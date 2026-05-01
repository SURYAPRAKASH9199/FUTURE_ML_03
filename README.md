# 🤖 Resume / Candidate Screening System
### Future Interns — Machine Learning Internship | Task 3 (2026)

---

> **"Instead of a recruiter reading 1000 resumes manually — this ML system does it in seconds!"**

---

## 📌 Table of Contents
1. [What is this project?](#-what-is-this-project)
2. [Real Life Problem it Solves](#-real-life-problem-it-solves)
3. [How it Works — Simple Explanation](#-how-it-works--simple-explanation)
4. [Features](#-features)
5. [Tech Stack](#-tech-stack)
6. [Datasets Used](#-datasets-used)
7. [Project Structure](#-project-structure)
8. [How to Run](#-how-to-run)
9. [How Scoring Works](#-how-scoring-works-the-brain-of-this-system)
10. [Output & Results](#-output--results)
11. [What I Learned](#-what-i-learned)

---

## 🎯 What is this project?

This is a **Machine Learning based Resume Screening System** that:

- 📄 Reads hundreds of resumes automatically
- 🔍 Extracts skills from each resume using **NLP (Natural Language Processing)**
- 📊 Compares each resume with a **Job Description**
- ⭐ Gives every candidate a **Score out of 100**
- 🏆 **Ranks candidates** — best fit at the top, worst fit at the bottom
- ❌ Tells you exactly **which skills are missing** in each resume

---

## 💼 Real Life Problem it Solves

Imagine you are an **HR Manager at TCS or Infosys.**

You post a job: **"Data Scientist Needed"**

**500 people apply. 500 resumes land in your inbox.**

```
❌ Reading all 500 manually = 3-4 days of work
❌ Missing good candidates by mistake
❌ Inconsistent evaluation — mood affects decisions
❌ Wasting recruiter time on clearly unfit resumes
```

**With this ML system:**

```
✅ All 500 resumes screened in under 1 minute
✅ Every candidate gets a fair, consistent score
✅ Top 10 candidates highlighted automatically
✅ Missing skills shown clearly for each person
✅ Recruiter only interviews the BEST candidates
```

This is exactly how **Naukri.com, LinkedIn, and HR-tech startups** work!

---

## 🧠 How it Works — Simple Explanation

```
STEP 1: Feed resumes into the system
         (We used 2484 real resumes from Kaggle)
              ↓
STEP 2: Clean the text
         (Remove emails, URLs, numbers, useless words)
              ↓
STEP 3: Extract Skills
         (Find: Python, SQL, TensorFlow, etc.)
              ↓
STEP 4: Compare with Job Description
         (Using TF-IDF — converts text to numbers)
              ↓
STEP 5: Calculate Score (0-100)
         (60% content match + 40% skill match)
              ↓
STEP 6: Rank all candidates
         (#1 = Best fit, #100 = Worst fit)
              ↓
STEP 7: Show results + charts + skill gaps
```

---

## ✨ Features

| Feature | Description |
|--------|-------------|
| 🧹 **Text Cleaning** | Removes URLs, emails, numbers, special characters |
| 🔍 **Skill Extraction** | Finds 80+ skills across 6 categories |
| 📊 **TF-IDF Scoring** | Converts text to numbers and finds similarity |
| 🏆 **Candidate Ranking** | Sorts candidates best to worst automatically |
| ❌ **Skill Gap Analysis** | Shows which required skills are missing |
| 📈 **4 Visual Charts** | Bar chart, histogram, score breakdown, skill gap |
| 💾 **CSV Export** | Results saved in Excel-friendly format |
| 🏷️ **Fit Labels** | Strong Fit 🟢 / Moderate 🟡 / Weak 🟠 / Not Fit 🔴 |

---

## 🛠️ Tech Stack

```
Language    →  Python 3.11
Notebook    →  Jupyter Notebook (in VS Code)
```

| Library | What it does in this project |
|---------|------------------------------|
| `pandas` | Load and handle CSV datasets |
| `numpy` | Numerical calculations |
| `scikit-learn` | TF-IDF vectorization + cosine similarity |
| `nltk` | Remove stopwords, tokenize text |
| `matplotlib` | Draw bar charts and histograms |
| `seaborn` | Make charts look beautiful |
| `re` | Clean text using regular expressions |

---

## 📁 Datasets Used

| # | Dataset | Source | What it's used for |
|---|---------|--------|-------------------|
| 1 | **Resume Dataset** | [Kaggle](https://www.kaggle.com/datasets/snehaanbhawal/resume-dataset) | 2484 real candidate resumes |
| 2 | **Job Descriptions** | [Kaggle](https://www.kaggle.com/datasets/ravindrasinghrana/job-description-dataset) | Real job role requirements |
| 3 | **Monster.com Jobs** | [Kaggle](https://www.kaggle.com/datasets/PromptCloudHQ/us-jobs-on-monstercom) | Real job postings as benchmark JD |

---

## 📂 Project Structure

```
FUTURE_ML_03/
│
├── 📁 data/                          ← All input datasets
│   ├── Resume.csv                    ← 2484 candidate resumes
│   ├── job_descriptions.csv          ← Job roles & skills
│   └── monster_com-job_sample.csv    ← Real Monster.com jobs
│
├── 📁 output/                        ← All results saved here
│   ├── candidate_rankings.csv        ← Full ranked list (Excel ready)
│   └── screening_results.png         ← 4 charts & visualizations
│
├── 📓 resume_screening.ipynb         ← MAIN NOTEBOOK (14 parts)
└── 📄 README.md                      ← This file
```

---

## 🚀 How to Run

### Step 1: Clone the repository
```bash
git clone https://github.com/SURYAPRAKASH9199/FUTURE_ML_03.git
cd FUTURE_ML_03
```

### Step 2: Install required libraries
```bash
pip install pandas numpy scikit-learn nltk matplotlib seaborn jupyter
```

### Step 3: Download datasets from Kaggle
Place these files inside the `data/` folder:
- `Resume.csv`
- `job_descriptions.csv`
- `monster_com-job_sample.csv`

### Step 4: Open the notebook
```bash
jupyter notebook resume_screening.ipynb
```

### Step 5: Run all cells
Click **"Run All"** — results will appear automatically! ✅

---

## 🧮 How Scoring Works (The Brain of this System)

### What is TF-IDF?

```
TF  = Term Frequency
      "How many times does 'Python' appear in this resume?"

IDF = Inverse Document Frequency
      "Is 'Python' a rare/important word or very common?"

TF-IDF = A number that tells us how IMPORTANT a word is
```

### Example:
```
Job Description says:  "Need Python, SQL, Machine Learning"
Candidate Resume says: "Python developer, knows SQL"

TF-IDF finds: 2 out of 3 keywords match → 66% similarity
```

### Final Score Formula:

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│   Final Score = (TF-IDF Score × 60%)               │
│               + (Skill Match Score × 40%)           │
│                                                     │
│   Example:                                          │
│   TF-IDF Score  = 70/100                           │
│   Skill Score   = 80/100                           │
│                                                     │
│   Final = (70×0.6) + (80×0.4)                      │
│         = 42 + 32                                   │
│         = 74/100 ← STRONG FIT 🟢                   │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### Fit Labels:
```
🟢 70-100  →  STRONG FIT   (Shortlist immediately!)
🟡 50-69   →  MODERATE FIT (Consider with caution)
🟠 30-49   →  WEAK FIT     (Needs significant training)
🔴 0-29    →  NOT FIT      (Does not match role)
```

---

## 📊 Output & Results

### Terminal Output Example:
```
============================================================
  🏆 TOP 10 CANDIDATES FOR: Data Scientist / ML Engineer
============================================================

#1 Candidate_15  [🟢 STRONG FIT]
   ⭐ Final Score    : 78.5 / 100
   📄 Content Match  : 82.3 / 100
   🛠️  Skill Match    : 72.0 / 100
   ✅ Matched Skills : python, machine learning, tensorflow, sql, pandas
   ❌ Missing Skills : aws, docker

#2 Candidate_3  [🟢 STRONG FIT]
   ⭐ Final Score    : 74.2 / 100
   ...
```

### Charts Generated:
```
Chart 1 → 🏆 Top 10 Candidates Bar Chart
Chart 2 → 📊 Score Breakdown (TF-IDF vs Skill)
Chart 3 → 📈 Score Distribution of All Candidates
Chart 4 → 🛠️ Skill Gap - Most Missing Skills
```

### CSV Output (candidate_rankings.csv):
```
Rank | Candidate    | Final_Score | Skill_Score | Matched_Skills      | Fit_Label
1    | Candidate_15 | 78.5        | 72.0        | python, sql, ml...  | Strong Fit
2    | Candidate_3  | 74.2        | 68.0        | python, tensorflow  | Strong Fit
...
```

---

## 🎓 What I Learned

Through this project, I learned:

```
✅ How to work with real-world unstructured text data
✅ NLP concepts: tokenization, stopword removal, TF-IDF
✅ How cosine similarity measures document similarity
✅ Skill extraction using keyword matching & regex
✅ How to build a complete ML pipeline end-to-end
✅ Data visualization with matplotlib & seaborn
✅ How real HR-tech systems work behind the scenes
✅ How to present ML results to non-technical users
```

---

## 👨‍💻 Author

**Surya Prakash**
Machine Learning Intern — Future Interns (2026)

[![GitHub](https://img.shields.io/badge/GitHub-SURYAPRAKASH9199-black?style=flat&logo=github)](https://github.com/SURYAPRAKASH9199)

---

## 🏢 About Future Interns

This project was built as part of the **Future Interns Machine Learning Track — Task 3**.

[![Future Interns](https://img.shields.io/badge/Future%20Interns-ML%20Track-blue?style=flat)](https://www.linkedin.com/company/future-interns/)

---

*"The best way to learn Machine Learning is to build something real — and this is real."* 🚀
