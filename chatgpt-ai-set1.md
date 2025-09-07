
## ✅ **AI, Machine Learning & NLP Interview Question Pack**

---

### **SECTION A – THEORY (10 marks)**

#### **Q1. Explain the difference between supervised, unsupervised, and reinforcement learning. Give an example of each.**

**Scoring Guide:**

* Correct definitions (3 marks)
* Relevant examples (3 marks)
* Key difference explained (2 marks)
* Mention real-world application (2 marks)

**Solution:**

* **Supervised:** Uses labeled data (e.g., spam detection).
* **Unsupervised:** Uses unlabeled data (e.g., clustering customers).
* **Reinforcement:** Agent learns by interacting with environment (e.g., game AI).

**Hint:** Think about presence/absence of labels and feedback mechanism.

**Follow-up:**

* Which method would you use for product recommendation?
* How does semi-supervised learning differ?

---

#### **Q2. What is the difference between Bag of Words (BoW) and TF-IDF in NLP?**

**Scoring Guide:**

* BoW explanation (2 marks)
* TF-IDF explanation (2 marks)
* Key difference (2 marks)
* Advantage of TF-IDF over BoW (2 marks)
* Real-world usage (2 marks)

**Solution:**

* BoW: Counts word frequency without context.
* TF-IDF: Weights words based on frequency and importance across documents.
* TF-IDF reduces the impact of common words like “the”, “is”.

**Hint:** TF-IDF = Term Frequency \* Inverse Document Frequency.

**Follow-up:**

* Why do we normalize TF-IDF values?
* How does Word2Vec differ from BoW?

---

---

### **SECTION B – PRACTICAL (20 marks)**

#### **Q3. Debugging: Find and fix the bug in the given ML model code (Python)**

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_test)
predictions = model.predict(X_test)
```

**Task:** Identify issues and fix them.

**Expected Fix:**

* The issue is that `y_test` is used instead of `y_train` for training. Correct code:

```python
model.fit(X_train, y_train)
```

**Scoring:**

* Identify wrong variable (5 marks)
* Explain why it’s wrong (5 marks)

**Follow-up:**

* What happens if you train on test data?
* Why do we split into train and test sets?

---

#### **Q4. Code Review: Optimize this text preprocessing pipeline**

```python
tokens = text.split()
tokens = [w.lower() for w in tokens]
clean_tokens = []
for t in tokens:
    if t not in stopwords:
        clean_tokens.append(t)
```

**Expected Optimizations:**

* Combine steps with list comprehension
* Use `re.sub` for better cleaning
* Use `nltk` or `spacy` for stopword removal

**Optimized Version:**

```python
import re
clean_tokens = [w.lower() for w in re.findall(r'\w+', text) if w.lower() not in stopwords]
```

**Follow-up:**

* How would you handle lemmatization?
* Why is tokenization important before vectorization?

---

---

### **SECTION C – PROGRAMMING (30 marks)**

#### **Q5. Implement a function to compute Cosine Similarity between two text documents.**

**Solution:**

```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.metrics.pairwise import cosine_similarity

def cosine_similarity_docs(doc1, doc2):
    vectorizer = CountVectorizer()
    vectors = vectorizer.fit_transform([doc1, doc2])
    return cosine_similarity(vectors[0], vectors[1])[0][0]
```

**Scoring:**

* Vectorization (10 marks)
* Cosine similarity computation (10 marks)
* Correct function structure (10 marks)

**Follow-up:**

* How would you improve this using TF-IDF instead of BoW?
* Why is cosine similarity used for text comparison?

---

#### **Q6. Implement a simple sentiment analysis model using Naive Bayes.**

**Solution:**

```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

texts = ["I love this movie", "I hate this movie"]
labels = [1, 0]

vectorizer = CountVectorizer()
X = vectorizer.fit_transform(texts)

model = MultinomialNB()
model.fit(X, labels)

test = vectorizer.transform(["This movie is great"])
print(model.predict(test))  # Expected output: [1]
```

**Scoring:**

* Data preparation (5 marks)
* Feature extraction (10 marks)
* Model training and prediction (10 marks)
* Handles unseen data (5 marks)

**Follow-up:**

* Why is Naive Bayes good for text classification?
* How would you handle imbalanced data?