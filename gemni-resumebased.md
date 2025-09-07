

# **Question Bank: Resume and Projects**

This section contains questions an interviewer might ask based on your **resume** and the **projects you've listed**. The goal is to understand your **experience**, your **role in the projects**, the **challenges you faced**, and **what you learned**.

---

## **Table of Contents**

- [**Question Bank: Resume and Projects**](#question-bank-resume-and-projects)
  - [**Table of Contents**](#table-of-contents)
  - [**Easy**](#easy)
    - [**Can you walk me through your resume?**](#can-you-walk-me-through-your-resume)
    - [**Tell me about a project you are most proud of.**](#tell-me-about-a-project-you-are-most-proud-of)
  - [**Medium**](#medium)
    - [**What was the most difficult challenge you faced during a specific project? How did you solve it?**](#what-was-the-most-difficult-challenge-you-faced-during-a-specific-project-how-did-you-solve-it)
    - [**Can you explain the architecture of a specific project?**](#can-you-explain-the-architecture-of-a-specific-project)
    - [**Describe a time you had a disagreement with a team member on a project. How did you handle it?**](#describe-a-time-you-had-a-disagreement-with-a-team-member-on-a-project-how-did-you-handle-it)
  - [**Difficult**](#difficult)
    - [**If you could start a specific project over again, what would you do differently?**](#if-you-could-start-a-specific-project-over-again-what-would-you-do-differently)
    - [**How did you test your project to ensure its quality?**](#how-did-you-test-your-project-to-ensure-its-quality)
    - [**How would you scale a specific project to handle 10x the current number of users?**](#how-would-you-scale-a-specific-project-to-handle-10x-the-current-number-of-users)

---

## **Easy**

### **Can you walk me through your resume?**

**Answer:**
Start with a brief **elevator pitch** about yourself:

* Your **major**
* Your **key interests** in software engineering
* What you're **passionate about**

Then, **chronologically walk through your experiences** (internships, projects, education), highlighting **1–2 key achievements** from each.
Keep it **concise (2–3 minutes)**.

**Hint:**
Don’t just **read your resume**. Tell a **story** that connects your experiences and shows **growth**.
Focus on **what you accomplished**, not just what you did.

**Follow-up:**
*"You mentioned \[specific project/skill], can you tell me more about that?"*

---

### **Tell me about a project you are most proud of.**

**Answer:**
Choose a project you can **talk about passionately**. Use the **STAR method**:

* **Situation:** What was the project goal?
* **Task:** What were you responsible for?
* **Action:** What actions did you take? (e.g., *"I designed REST API endpoints using Node.js and Express"*)
* **Result:** What was the outcome? (e.g., *"Reduced response time by 20%"* or *"Got 100 beta users"*)

**Hint:**
Pick a project that shows a **good range of technical skills** and **problem-solving abilities**.

**Follow-up:**
*"What was the biggest technical challenge you faced in this project?"*

---

## **Medium**

### **What was the most difficult challenge you faced during a specific project? How did you solve it?**

**Answer:**
Be **specific**. Avoid generic answers like *"debugging was hard."*
A good example:
*"In the e-commerce project, we faced a challenge with database query performance under heavy load. I optimized it by adding indexes on frequently queried columns and implemented Redis caching for popular product data. This reduced query time from 200ms to under 50ms."*

**Hint:**
Focus on a **technical challenge**. Show **problem-solving skills** and **technical depth**.

**Follow-up:**
*"What other alternative solutions did you consider? Why did you choose this one?"*

---

### **Can you explain the architecture of a specific project?**

**Answer:**
Example for a web app:
\*"It was a 3-tier architecture:

* Frontend: React
* Backend: Node.js (REST APIs)
* Database: MongoDB
  Deployed on AWS (EC2 for server, S3 for static assets)."\*

**Hint:**
Be ready to go **deep into any part** you mention.

**Follow-up:**
*"Why did you choose MongoDB over PostgreSQL?"*

---

### **Describe a time you had a disagreement with a team member on a project. How did you handle it?**

**Answer:**
Focus on **technical disagreement**, e.g.:
*"My teammate wanted to use polling for real-time updates, but I suggested WebSockets. I created a proof-of-concept showing better performance and resource efficiency. We agreed to use WebSockets after reviewing data."*

**Hint:**
Show **effective communication** and **data-driven decisions**.

---

## **Difficult**

### **If you could start a specific project over again, what would you do differently?**

**Answer:**
*"We didn’t spend enough time defining the database schema. We chose NoSQL for flexibility, but later realized a relational model would enforce data integrity better. Next time, I’d invest more in upfront data modeling and use PostgreSQL for ACID properties."*

**Hint:**
Show **self-awareness** and **continuous improvement**.

**Follow-up:**
*"How would that have impacted the project timeline and complexity?"*

---

### **How did you test your project to ensure its quality?**

**Answer:**

* **Backend:** Unit tests with **Jest**, integration tests for APIs
* **Frontend:** Component tests with **React Testing Library**
* **End-to-End:** Manual + automated tests
* **CI/CD:** GitHub Actions to run tests on every commit

**Hint:**
Mention **automated testing** and **CI/CD** for credibility.

**Follow-up:**
*"What was your code coverage? How did you handle a critical bug after deployment?"*

---

### **How would you scale a specific project to handle 10x the current number of users?**

**Answer:**
Break down **bottlenecks**:

* **Database:** Add read replicas
* **Backend:** Containerize with **Docker**, deploy on **Kubernetes**, scale horizontally
* **Frontend:** Use a **CDN** for static assets

**Hint:**
Mention **load balancer**, **caching**, and **scalability strategies**.

**Follow-up:**
*"What kind of load balancer would you use? Horizontal vs Vertical scaling trade-offs?"*