# 🎯 Software Engineer Campus Placement – Full Interview Prep Kit  

---

## 1. Resume-Based Questions  

### Q1: Walk me through your resume.  
**Sample Answer (STAR-aligned):**  
- **Situation:** I’m a final-year Computer Science student with internship experience at XYZ Corp.  
- **Task:** I’ve focused on full-stack projects and algorithmic problem-solving.  
- **Action:** Built scalable web applications using React and Node.js, optimized DB queries, solved 500+ DSA problems.  
- **Result:** My work reduced API response times by 20% and improved team efficiency.  

**Hint:** Keep it under 2 minutes, highlight 2–3 strongest achievements.  

**Evaluation Criteria:**  
- Clarity of narrative (0–100)  
- Technical alignment with job (0–100)  
- Confidence & structure (0–100)  

**Follow-up:**  
- Which project in your resume best demonstrates your coding ability?  

---

## 2. Project-Based Questions  

### Q2: What challenges did you face in your project and how did you solve them?  
**Sample Answer:**  
During my e-commerce project, I faced performance issues due to inefficient SQL queries. I optimized by introducing indexing and caching (Redis), reducing page load time from 3s to 800ms.  

**Hint:** Pick ONE challenge → Describe → Solution → Quantify impact.  

**Evaluation Criteria:**  
- Depth of challenge (0–100)  
- Problem-solving ability (0–100)  
- Measurable impact (0–100)  

**Follow-up:**  
- If this project had 10x traffic, how would you redesign it?  

---

## 3. Core Computer Engineering Concepts  

### OOP Example Question  
**Q3: Explain the difference between abstract class and interface.**  

**Sample Answer:**  
- Abstract class → can have both abstract and concrete methods.  
- Interface → defines contract, no implementation (before Java 8).  
- Use abstract class when you want partial implementation, interface for pure abstraction.  

**Hint:** Mention Java 8+ default methods in interfaces.  

**Evaluation Criteria:**  
- Correctness of concept (0–100)  
- Example provided (0–100)  

**Follow-up:**  
- Can a class implement multiple interfaces? Why?  

---

## 4. Coding Questions  

### Easy – Strings  

**Q4: Reverse a string**  
```python
def reverse_string(s: str) -> str:
    return s[::-1]
````

**Hint:** Think about in-place reversal with two pointers.

**Evaluation Criteria:**

* Correctness (0–100)
* Time complexity awareness (0–100)

**Follow-up:**

* Can you reverse it **without using extra space**?

---

### Medium – HashMap

**Q5: Group Anagrams**

```python
from collections import defaultdict
def groupAnagrams(strs):
    groups = defaultdict(list)
    for s in strs:
        groups["".join(sorted(s))].append(s)
    return list(groups.values())
```

**Hint:** Key is to map sorted string to group.

**Evaluation Rubric:**

* Optimal approach (O(n\*k log k))
* Use of hashing
* Edge cases

**Follow-up:**

* Can you do this without sorting each string?

---

### Hard – LRU Cache (Design)

**Q6: Implement LRU Cache**

* Use **HashMap + Doubly Linked List**.
* HashMap → O(1) lookup.
* DLL → O(1) eviction & reordering.

**Evaluation Criteria:**

* Correct DS choice (0–100)
* Code quality (0–100)
* Edge handling (0–100)

**Follow-up:**

* How would you scale this for distributed cache (like Redis)?

---

## 5. System Design

### Q7: Design a URL Shortener (like Bitly)

**Approach:**

* **Requirement Gathering:** High availability, low latency, unique short links.
* **High-Level Design:**

  * API layer → Generate/Resolve URLs.
  * DB → Map short → long.
  * Hashing/ID generator for short links.
  * Cache (Redis) for hot URLs.

**Hint:** Mention base62 encoding.

**Evaluation Criteria:**

* Coverage of requirements (0–100)
* Scalability awareness (0–100)
* Clear trade-offs (0–100)

**Follow-up:**

* How do you prevent collisions in hash-based short links?

---

## 6. AI & LLM

### Q8: What are hallucinations in LLMs?

**Sample Answer:**
Hallucinations are cases where an LLM generates output that is fluent but factually incorrect. This happens due to training limitations, lack of grounding in factual data, or overgeneralization.

**Evaluation Criteria:**

* Technical depth (0–100)
* Example clarity (0–100)

**Follow-up:**

* How would you reduce hallucinations in production LLMs?

---