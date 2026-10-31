# COMP5313 – Project 2: Word Embedding for Sentiment Analysis

## What is this project about?

We want a computer to read a **movie review** and decide if it is
**positive** 👍 or **negative** 👎.

Computers can't understand words directly, so we first turn the words into
**numbers**. This is called **word embedding**. Then a simple classifier
(Logistic Regression) learns from those numbers.

We will try **two different ways** of turning words into numbers and check
**which one is more accurate**.

## The dataset

- **IMDb movie reviews** (`stanfordnlp/imdb` on Hugging Face)
- 25,000 reviews for training and 25,000 for testing
- Each review is labeled **positive (1)** or **negative (0)**

## The two methods we compare

### Method 1: TF-IDF + Logistic Regression (the baseline)
- Counts how often each word appears in a review.
- Gives **less importance** to very common words like "the", "and", "is".
- Very fast (trains in a few seconds on a normal laptop).
- Expected accuracy: **about 80–85%**.
- Weakness: it doesn't know that "fantastic" and "spectacular" mean almost
  the same thing.

### Method 2: choose ONE of these
**Option A: GloVe + Logistic Regression** (recommended, works on a normal CPU)
- GloVe is a set of **pre-trained word vectors**. Every word already has a
  list of numbers that captures its meaning.
- Similar words have similar numbers, so "fantastic" ≈ "spectacular".
- For each review, we **average** the vectors of its words to get one vector.
- Still fast, and no GPU is needed.

**Option B: BERT**
- A large, powerful transformer model that understands words **in context**.
- Usually the most accurate, but **slow** and works best with a GPU.

## Steps to do

1. **Load** the IMDb dataset.
2. **Clean** the text (lowercase, remove HTML tags like `<br />`, etc.).
3. **Method 1:** build TF-IDF features → train Logistic Regression → get accuracy.
4. **Method 2:** build GloVe (or BERT) features → train the classifier → get accuracy.
5. **Compare** the two accuracies (a small table and/or bar chart).
6. **Take screenshots** of the outputs and save them in `screenshots/`.
7. **Write the ReadMe.pdf** explaining the idea and results.
8. **Zip** everything and submit it on D2L.

## Project files

| File / Folder              | What it is                                         |
|----------------------------|----------------------------------------------------|
| `YourName_Project2.ipynb`  | The main notebook with all the code (rename it with your name) |
| `requirements.txt`         | List of Python libraries needed                    |
| `screenshots/`             | Screenshots of the program outputs                 |
| `README.md`                | This file (simple project notes)                   |
| `ReadMe.pdf`               | Final write-up for submission (to be created)      |

## Submission checklist

- [ ] Notebook renamed to `<YourName>_Project2.ipynb`
- [ ] Notebook runs from top to bottom without errors
- [ ] Both accuracies are printed and compared
- [ ] Screenshots of outputs taken
- [ ] `ReadMe.pdf` written (**PDF only, not Word**)
- [ ] Everything packed into **one `.zip` file** (**not RAR**)
- [ ] Submitted on **D2L before the deadline** (−1 mark per hour late, up to 3 hours)
