# Question Bank: Artificial Intelligence (AI) and Large Language Models (LLMs)

This section contains questions about the rapidly evolving fields of AI, Machine Learning (ML), and Large Language Models (LLMs). Questions range from high-level concepts to more specific details about LLMs.

---

## **Table of Contents**
- [Question Bank: Artificial Intelligence (AI) and Large Language Models (LLMs)](#question-bank-artificial-intelligence-ai-and-large-language-models-llms)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**Question:** What is the difference between Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning (DL)?](#question-what-is-the-difference-between-artificial-intelligence-ai-machine-learning-ml-and-deep-learning-dl)
    - [**Question:** What is a Large Language Model (LLM)?](#question-what-is-a-large-language-model-llm)
    - [**Question:** What is "prompt engineering"?](#question-what-is-prompt-engineering)
  - [**Medium**](#medium)
    - [**Question:** What is a transformer architecture and why is it important for LLMs?](#question-what-is-a-transformer-architecture-and-why-is-it-important-for-llms)
    - [**Question:** What is the difference between supervised and unsupervised learning in machine learning?](#question-what-is-the-difference-between-supervised-and-unsupervised-learning-in-machine-learning)
    - [**Question:** What are "hallucinations" in the context of LLMs?](#question-what-are-hallucinations-in-the-context-of-llms)
  - [**Difficult**](#difficult)
    - [**Question:** What is Retrieval-Augmented Generation (RAG)?](#question-what-is-retrieval-augmented-generation-rag)
    - [**Question:** What are vector embeddings and why are they important in AI?](#question-what-are-vector-embeddings-and-why-are-they-important-in-ai)
    - [**Question:** Explain the concept of "fine-tuning" an LLM.](#question-explain-the-concept-of-fine-tuning-an-llm)

---

## **Easy**

### **Question:** What is the difference between Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning (DL)?

**Answer:**  
They are subsets of one another:
- **AI (Artificial Intelligence):** Broadest field. Creating machines that can simulate human intelligence, reasoning, and behavior.
- **ML (Machine Learning):** Subset of AI where algorithms learn patterns from data instead of being explicitly programmed.
- **DL (Deep Learning):** Subset of ML using multi-layered neural networks to learn from large data. Powers image recognition and LLMs.

**Hint:**  
Think of them as **Russian nesting dolls**:  
AI → ML → DL.

---

### **Question:** What is a Large Language Model (LLM)?

**Answer:**  
An LLM is a type of **deep learning model** trained on massive amounts of text data to **understand and generate human-like language**.  
- Called **"large"** because of **billions/trillions of parameters** and training on **terabytes of data**.
- Examples: **OpenAI GPT series, Google Gemini, Meta LLaMA**.

**Hint:**  
It’s a **huge neural network that has read most of the internet** and learned language patterns.

---

### **Question:** What is "prompt engineering"?

**Answer:**  
Prompt engineering is the **art and science of crafting effective inputs (prompts)** to guide an LLM to produce desired outputs.  
- Good prompts provide **clear instructions, context, and examples**.
- Quality of input heavily influences output.

**Hint:**  
Like being a **good manager** giving clear instructions to a very literal assistant.

---

## **Medium**

### **Question:** What is a transformer architecture and why is it important for LLMs?

**Answer:**  
Introduced in **“Attention Is All You Need” (2017)**, the **transformer architecture** is the foundation of modern LLMs.  
- **Key innovation:** **Self-attention mechanism**  
- Unlike RNNs (sequential), transformers **process words in parallel** and **capture long-range dependencies**.
- Enables **scalability** and **better context understanding**.

**Hint:**  
The magic word is **attention**—the model looks at the entire sentence at once to decide importance.

---

### **Question:** What is the difference between supervised and unsupervised learning in machine learning?

**Answer:**  
- **Supervised Learning:**  
  - Uses **labeled data** (input → correct output).  
  - Examples: **Image classification, spam detection**.  
- **Unsupervised Learning:**  
  - Uses **unlabeled data**. Finds **patterns or clusters** without predefined labels.  
  - Examples: **Clustering customers, dimensionality reduction**.  

**Hint:**  
Supervised = **teacher gives answers**.  
Unsupervised = **explore data on your own**.  
Pre-training of LLMs is largely **self-supervised**.

---

### **Question:** What are "hallucinations" in the context of LLMs?

**Answer:**  
A hallucination occurs when an LLM generates **factually incorrect or nonsensical text** but presents it **confidently**.  
- Happens because LLMs **predict next words probabilistically**, not based on true facts.  
- Major limitation of LLMs.

**Hint:**  
The model is just **guessing what sounds right**, not verifying facts.

**Follow-up:**  
How can you mitigate hallucinations? (e.g., **RAG**).

---

## **Difficult**

### **Question:** What is Retrieval-Augmented Generation (RAG)?

**Answer:**  
RAG combines **retrieval + generation** to improve LLM accuracy:
1. **Retrieval:** Find relevant info from external knowledge base using vector search.
2. **Generation:** Provide retrieved info to LLM in the prompt for **grounded, accurate answers**.

**Benefits:**  
- Reduces **hallucinations**.  
- Allows access to **up-to-date or proprietary info**.  
- Enables **source citation**.

**Hint:**  
It’s like giving the LLM an **open-book exam**.

---

### **Question:** What are vector embeddings and why are they important in AI?

**Answer:**  
Vector embeddings = **numerical representations** of words, sentences, or images in multi-dimensional space.  
- **Similar items → closer in vector space**.  
- Learned by neural networks.

**Importance:**  
- Captures **semantic meaning** (e.g., king ≈ queen, not apple).  
- Converts unstructured data → **machine-readable format**.  
- Essential for **semantic search, recommendations, RAG**.

**Hint:**  
Like putting words as **coordinates on a map** where similar meanings live close.

---

### **Question:** Explain the concept of "fine-tuning" an LLM.

**Answer:**  
Fine-tuning = **adapting a pre-trained LLM** for a **specific task or domain**:
- Start with **general-purpose model**.
- Train further on **specialized dataset** (e.g., legal docs, customer support chats).
- Requires **less data and compute** than training from scratch.

**Hint:**  
Like a **college graduate** going to **law school** to specialize.

**Follow-up:**  
What are techniques for **parameter-efficient fine-tuning (PEFT)**, like **LoRA**?

---
