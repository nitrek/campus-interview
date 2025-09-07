Question Bank: Artificial Intelligence (AI) and Large Language Models (LLMs)
This section contains questions about the rapidly evolving fields of AI, Machine Learning (ML), and Large Language Models (LLMs). Questions range from high-level concepts to more specific details about LLMs.
Easy
Question: What is the difference between Artificial Intelligence (AI), Machine Learning (ML), and Deep Learning (DL)?
Answer: They are subsets of one another.
AI (Artificial Intelligence) is the broadest field. It's the overall concept of creating machines that can simulate human intelligence, reasoning, and behavior.
ML (Machine Learning) is a subset of AI. Instead of being explicitly programmed, ML algorithms are "trained" on large amounts of data to learn patterns and make predictions or decisions.
DL (Deep Learning) is a specialized subset of ML. It uses complex, multi-layered neural networks (hence "deep") to learn from vast amounts of data. Deep learning is the technology behind many recent breakthroughs, including advanced image recognition and large language models.
Hint: Think of them as Russian nesting dolls. AI is the biggest doll, ML is inside AI, and DL is inside ML.
Question: What is a Large Language Model (LLM)?
Answer: An LLM is a type of deep learning model that has been trained on massive amounts of text data to understand and generate human-like language. They are called "large" because they have an enormous number of parameters (billions or even trillions) and are trained on terabytes of data from the internet, books, and other sources. Examples include OpenAI's GPT series, Google's Gemini, and Meta's Llama.
Hint: It's a very big neural network that has read a significant portion of the internet and learned the patterns of language.
Question: What is "prompt engineering"?
Answer: Prompt engineering is the art and science of designing effective inputs (prompts) to guide an LLM to produce a desired output. Since the quality and specificity of the input prompt heavily influence the model's response, carefully crafting the prompt—by providing clear instructions, context, and examples—is crucial for getting accurate, relevant, and useful results.
Hint: It's like being a good manager. You have to give clear and specific instructions to your highly capable but very literal assistant (the LLM).
Medium
Question: What is a transformer architecture and why is it important for LLMs?
Answer: The transformer architecture is a neural network design, introduced in the 2017 paper "Attention Is All You Need." It has become the foundational architecture for nearly all modern LLMs.
Its key innovation is the self-attention mechanism. Unlike previous models (like RNNs) that processed text sequentially, the attention mechanism allows the model to weigh the importance of different words in the input text simultaneously, regardless of their position. This enables it to capture long-range dependencies and understand the context of a word by "paying attention" to all other words in the sequence. This parallel processing capability and superior contextual understanding are what allowed models to be scaled up to the massive size of today's LLMs.
Hint: The key is "attention." It lets the model look at the entire sentence at once and figure out which words are most important for understanding any given word. This is much more effective than reading word by word.
Question: What is the difference between supervised and unsupervised learning in machine learning?
Answer:
Supervised Learning: In supervised learning, the model is trained on a labeled dataset. This means that each piece of training data has a corresponding correct "output" or "label." The model's goal is to learn a mapping function that can predict the output label for new, unseen data.
Examples: Image classification (training with images labeled "cat" or "dog"), spam detection (emails labeled "spam" or "not spam").
Unsupervised Learning: In unsupervised learning, the model is trained on an unlabeled dataset. The model tries to find patterns, structures, and relationships within the data on its own, without any predefined correct answers.
Examples: Clustering (grouping similar customers together based on purchasing behavior), dimensionality reduction.
Hint: Supervised learning is like learning with a teacher who provides the answers. Unsupervised learning is like being given a pile of data and told to "find something interesting." The pre-training of LLMs is largely an unsupervised (or self-supervised) task.
Question: What are "hallucinations" in the context of LLMs?
Answer: A hallucination is when an LLM generates text that is factually incorrect, nonsensical, or completely fabricated, yet presents it confidently as if it were true. This happens because LLMs are probabilistic models designed to predict the next most likely word in a sequence based on their training data; they do not have a true understanding of facts or a connection to the real world. They are pattern matchers, not fact-checkers. Hallucinations are a major challenge and limitation of current LLM technology.
Hint: The model is just guessing the next word that "sounds" right based on patterns, not because it "knows" it's a fact.
Follow-up: "How can you mitigate hallucinations when using an LLM in an application?" (e.g., using Retrieval-Augmented Generation - RAG).
Difficult
Question: What is Retrieval-Augmented Generation (RAG)?
Answer: RAG is a technique used to improve the accuracy and reliability of LLMs by grounding their responses in external, up-to-date, or proprietary knowledge.
The process works in two stages:
Retrieval: When a user asks a question, the RAG system first searches an external knowledge base (like a set of company documents, a technical manual, or a database) to find information relevant to the user's query. This is often done by converting the query and the documents into vector embeddings and finding the most similar documents.
Generation: The relevant information retrieved in the first step is then passed to the LLM as part of the context in the prompt, along with the original question. The LLM then uses this provided context to generate its answer.
This helps to reduce hallucinations, allows the LLM to answer questions about information it wasn't trained on, and provides a way to cite sources for its answers.
Hint: It's like giving the LLM an "open book" for its exam. Instead of just relying on its memory (training data), it first looks up the answer in a specific, trusted book (the knowledge base) and then formulates the answer.
Question: What are vector embeddings and why are they important in AI?
Answer: Vector embeddings are numerical representations of data, such as words, sentences, or images, in a multi-dimensional space. The key idea is that similar or related items will be located closer to each other in this vector space. These embeddings are learned by neural networks.
Why they are important:
Semantic Understanding: They capture the semantic meaning and context of data. For example, the vectors for "king" and "queen" will be closer than the vectors for "king" and "apple."
Machine Readability: They convert complex, unstructured data (like text) into a fixed-size numerical format that machine learning models can easily process.
Applications: They are fundamental to many AI tasks, including semantic search (finding documents based on meaning, not just keywords), recommendation systems, text classification, and the retrieval step in RAG systems.
Hint: It's a way to turn words into coordinates on a map. Words with similar meanings are placed in the same neighborhood on the map.
Question: Explain the concept of "fine-tuning" an LLM.
Answer: Fine-tuning is the process of taking a large, pre-trained language model and training it further on a smaller, specific dataset to adapt it for a particular task or domain. The pre-trained model has already learned general language patterns from its massive initial training. Fine-tuning adjusts the model's weights to specialize in a narrower task.
For example, you could take a general-purpose LLM and fine-tune it on a dataset of legal documents to make it better at legal language analysis, or fine-tune it on a dataset of customer support conversations to create a specialized chatbot. Fine-tuning requires significantly less data and computational resources than training a model from scratch.
Hint: The pre-trained model is like a college graduate with a broad education. Fine-tuning is like sending them to law school or medical school to become a specialist in a specific field.
Follow-up: "What are some techniques for parameter-efficient fine-tuning (PEFT), like LoRA?"
