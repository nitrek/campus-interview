# Comprehensive Campus Placement Question Bank for Software Engineers

## Table of Contents
1. [Resume & Project Questions](#resume--project-questions)
2. [Computer Engineering Theory Questions](#computer-engineering-theory-questions)
3. [AI/LLM Questions](#aillm-questions)
4. [Coding Questions](#coding-questions)
   - [String Questions](#string-questions)
   - [Hash Map Questions](#hash-map-questions)
   - [Data Structures Questions](#data-structures-questions)
5. [System Design Questions](#system-design-questions)
6. [Behavioral Questions](#behavioral-questions)

---

## Resume & Project Questions

### Resume-Based Questions
1. **Tell me about yourself.**
   - *Tip: Keep it professional, focus on relevant experience and skills*

2. **Walk me through your resume.**
   - *Prepare a 2-3 minute narrative highlighting key experiences*

3. **What is your biggest achievement highlighted on your resume?**
   - *Use STAR method: Situation, Task, Action, Result*

4. **Explain any gaps or low scores in your academic record.**
   - *Be honest and focus on what you learned*

5. **Which skills on your resume are you most confident about?**
   - *Choose skills with concrete examples*

### Project-Based Questions
1. **Describe your favorite project in detail.**
   - *Cover: Problem, Solution, Technology Stack, Challenges*

2. **What challenges did you face during your project and how did you overcome them?**
   - *Focus on problem-solving approach*

3. **Why did you choose this particular technology stack?**
   - *Justify technical decisions*

4. **How did you handle version control in your project?**
   - *Mention Git, branching strategies*

5. **What would you do differently if you were to restart this project?**
   - *Shows learning and improvement mindset*

6. **How did you test your application?**
   - *Unit testing, integration testing, manual testing*

7. **What was the most complex feature you implemented?**
   - *Technical depth and problem-solving*

8. **How did you ensure code quality in your project?**
   - *Code reviews, linting, best practices*

---

## Computer Engineering Theory Questions

### Operating Systems
1. **What is the difference between process and thread?**
   - Process: Independent execution unit with separate memory space
   - Thread: Lightweight process sharing memory space

2. **Explain different states of a process.**
   - New, Ready, Running, Waiting, Terminated

3. **What is a deadlock? How can you prevent it?**
   - Deadlock: Circular wait for resources
   - Prevention: Avoid circular wait, preemption, hold and wait

4. **Difference between preemptive and non-preemptive scheduling.**
   - Preemptive: OS can interrupt running process
   - Non-preemptive: Process runs until completion or blocking

### Computer Networks
1. **Explain the OSI model layers.**
   - Physical, Data Link, Network, Transport, Session, Presentation, Application

2. **TCP vs UDP - differences and use cases.**
   - TCP: Reliable, connection-oriented, slower
   - UDP: Unreliable, connectionless, faster

3. **What happens when you type a URL in a browser?**
   - DNS resolution, TCP connection, HTTP request, response processing

4. **Explain HTTP status codes.**
   - 200 (OK), 404 (Not Found), 500 (Internal Server Error)

### Database Management Systems
1. **What is normalization? Explain different normal forms.**
   - 1NF: Atomic values
   - 2NF: No partial dependency
   - 3NF: No transitive dependency

2. **Explain ACID properties.**
   - Atomicity, Consistency, Isolation, Durability

3. **Difference between SQL and NoSQL databases.**
   - SQL: Structured, ACID compliance, relational
   - NoSQL: Flexible schema, horizontal scaling, document/key-value

4. **What is indexing and how does it improve performance?**
   - Creates separate structure for faster data retrieval

### Object-Oriented Programming
1. **What are the four pillars of OOP?**
   - Encapsulation, Inheritance, Polymorphism, Abstraction

2. **Explain polymorphism with examples.**
   - Method overriding (runtime) and method overloading (compile time)

3. **Abstract classes vs Interfaces.**
   - Abstract: Can have implementation, single inheritance
   - Interface: Contract definition, multiple inheritance

4. **What is method overriding vs method overloading?**
   - Overriding: Same signature in child class
   - Overloading: Same name, different parameters

---

## AI/LLM Questions

### Basic AI Concepts
1. **What is Artificial Intelligence? Name some real-world applications.**
   - AI: Machines performing human-like tasks
   - Applications: Chatbots, recommendation systems, autonomous vehicles

2. **Difference between AI, Machine Learning, and Deep Learning.**
   - AI ⊃ ML ⊃ DL (AI contains ML, ML contains DL)

3. **What are the types of machine learning?**
   - Supervised, Unsupervised, Reinforcement Learning

4. **Explain supervised vs unsupervised learning with examples.**
   - Supervised: Has labeled data (classification, regression)
   - Unsupervised: No labels (clustering, dimensionality reduction)

### Machine Learning
1. **What is overfitting and how can you avoid it?**
   - Model memorizes training data, poor generalization
   - Solutions: Cross-validation, regularization, more data

2. **Explain bias-variance tradeoff.**
   - Bias: Underfitting, Variance: Overfitting
   - Goal: Balance between both

3. **What is the difference between classification and regression?**
   - Classification: Predict categories
   - Regression: Predict continuous values

4. **Explain gradient descent.**
   - Optimization algorithm to minimize cost function
   - Updates parameters in direction of steepest descent

### Large Language Models (LLMs)
1. **What are Large Language Models?**
   - Neural networks trained on vast text data for language understanding

2. **Explain the Transformer architecture.**
   - Encoder-decoder architecture using attention mechanisms
   - Parallel processing, no recurrence

3. **What is the attention mechanism?**
   - Allows model to focus on relevant parts of input sequence
   - Query, Key, Value vectors compute attention scores

4. **Explain self-attention in transformers.**
   - Attention applied within single sequence
   - Determines relationships between words in same sentence

5. **What is prompt engineering?**
   - Crafting effective prompts to get desired outputs from LLMs

6. **Difference between BERT and GPT.**
   - BERT: Bidirectional, encoder-only, understanding tasks
   - GPT: Autoregressive, decoder-only, generation tasks

7. **What are attention weights and why are they useful?**
   - Represent focus model gives to each token
   - Help understand model decisions and dependencies

---

## Coding Questions

### String Questions

#### Easy Level
1. **Reverse a string**
   - *Hint: Two pointers approach*
   - *Example: "hello" → "olleh"*
   - *Follow-up: Do it in-place*
   ```python
   def reverse_string(s):
       return s[::-1]  # Or use two pointers
   ```

2. **Check if string is palindrome**
   - *Hint: Compare characters from start and end*
   - *Example: "madam" → True*
   - *Follow-up: Ignore spaces and case*
   ```python
   def is_palindrome(s):
       left, right = 0, len(s) - 1
       while left < right:
           if s[left] != s[right]:
               return False
           left += 1
           right -= 1
       return True
   ```

3. **Count vowels in a string**
   - *Hint: Check each character against vowel set*
   - *Example: "hello" → 2*
   - *Follow-up: Handle both cases*

4. **Remove duplicates from string**
   - *Hint: Use set or frequency map*
   - *Example: "programming" → "progamin"*
   - *Follow-up: Preserve order*

#### Medium Level
1. **Longest substring without repeating characters**
   - *Hint: Sliding window with HashMap*
   - *Example: "abcabcbb" → 3 ("abc")*
   - *Follow-up: Return the actual substring*
   ```python
   def longest_unique_substring(s):
       char_map = {}
       left = max_length = 0
       for right in range(len(s)):
           if s[right] in char_map:
               left = max(left, char_map[s[right]] + 1)
           char_map[s[right]] = right
           max_length = max(max_length, right - left + 1)
       return max_length
   ```

2. **Group anagrams**
   - *Hint: Use sorted string as key*
   - *Example: ["eat","tea","tan","ate","nat","bat"] → [["ate","eat","tea"],["nat","tan"],["bat"]]*
   - *Follow-up: Optimize sorting*

3. **Valid parentheses**
   - *Hint: Use stack*
   - *Example: "()[]{}" → True*
   - *Follow-up: Handle nested parentheses*

4. **String to integer (atoi)**
   - *Hint: Handle edge cases (whitespace, signs, overflow)*
   - *Example: "42" → 42*
   - *Follow-up: Handle different bases*

#### Hard Level
1. **Minimum window substring**
   - *Hint: Sliding window with frequency count*
   - *Example: s="ADOBECODEBANC", t="ABC" → "BANC"*
   - *Follow-up: What if multiple windows exist?*

2. **Edit distance**
   - *Hint: Dynamic programming*
   - *Example: "horse" to "ros" → 3 operations*
   - *Follow-up: Return actual operations*

3. **Regular expression matching**
   - *Hint: Dynamic programming with pattern matching*
   - *Example: s="aa", p="a*" → True*
   - *Follow-up: Handle different regex patterns*

### Hash Map Questions

#### Easy Level
1. **Two sum**
   - *Hint: Store complement in HashMap*
   - *Example: [2,7,11,15], target=9 → [0,1]*
   - *Follow-up: Find all pairs that sum to target*
   ```python
   def two_sum(nums, target):
       num_map = {}
       for i, num in enumerate(nums):
           complement = target - num
           if complement in num_map:
               return [num_map[complement], i]
           num_map[num] = i
   ```

2. **Valid anagram**
   - *Hint: Count character frequencies*
   - *Example: "anagram", "nagaram" → True*
   - *Follow-up: Handle Unicode characters*

3. **Contains duplicate**
   - *Hint: Use set to track seen elements*
   - *Example: [1,2,3,1] → True*
   - *Follow-up: Find the duplicate within k distance*

#### Medium Level
1. **Group anagrams**
   - *Hint: Use sorted string or character count as key*
   - *Example: ["eat","tea","tan"] → [["eat","tea"],["tan"]]*
   - *Follow-up: Optimize for large inputs*

2. **Subarray sum equals K**
   - *Hint: Prefix sum with HashMap*
   - *Example: [1,1,1], k=2 → 2*
   - *Follow-up: Handle negative numbers*
   ```python
   def subarray_sum(nums, k):
       count = 0
       prefix_sum = 0
       sum_map = {0: 1}
       for num in nums:
           prefix_sum += num
           if prefix_sum - k in sum_map:
               count += sum_map[prefix_sum - k]
           sum_map[prefix_sum] = sum_map.get(prefix_sum, 0) + 1
       return count
   ```

3. **Top K frequent elements**
   - *Hint: HashMap + heap or bucket sort*
   - *Example: [1,1,1,2,2,3], k=2 → [1,2]*
   - *Follow-up: Handle ties*

#### Hard Level
1. **Longest consecutive sequence**
   - *Hint: HashSet for O(1) lookup*
   - *Example: [100,4,200,1,3,2] → 4*
   - *Follow-up: Return the actual sequence*

2. **First missing positive**
   - *Hint: Use array indices as hash map*
   - *Example: [3,4,-1,1] → 2*
   - *Follow-up: Handle duplicates*

### Data Structures Questions

#### Arrays
**Easy:**
1. **Find maximum element in array**
   - *Hint: Single pass*
   - *Example: [3,5,2,9,1] → 9*
   - *Follow-up: Find second maximum*

2. **Rotate array by k positions**
   - *Hint: Reverse subarrays*
   - *Example: [1,2,3,4,5], k=2 → [4,5,1,2,3]*
   - *Follow-up: Rotate in-place*

**Medium:**
1. **Maximum subarray sum (Kadane's algorithm)**
   - *Hint: Track current and maximum sum*
   - *Example: [-2,1,-3,4,-1,2,1,-5,4] → 6*
   - *Follow-up: Return the subarray indices*

2. **Product of array except self**
   - *Hint: Left and right pass*
   - *Example: [1,2,3,4] → [24,12,8,6]*
   - *Follow-up: Use O(1) extra space*

**Hard:**
1. **Trapping rainwater**
   - *Hint: Two pointers or precompute max heights*
   - *Example: [0,1,0,2,1,0,1,3,2,1,2,1] → 6*
   - *Follow-up: 2D version*

#### Linked Lists
**Easy:**
1. **Reverse linked list**
   - *Hint: Three pointers (prev, curr, next)*
   - *Follow-up: Reverse recursively*
   ```python
   def reverse_list(head):
       prev = None
       curr = head
       while curr:
           next_temp = curr.next
           curr.next = prev
           prev = curr
           curr = next_temp
       return prev
   ```

2. **Merge two sorted lists**
   - *Hint: Two pointers*
   - *Follow-up: Merge k sorted lists*

**Medium:**
1. **Detect cycle in linked list**
   - *Hint: Floyd's cycle-finding algorithm (tortoise and hare)*
   - *Follow-up: Find the start of cycle*

2. **Remove nth node from end**
   - *Hint: Two pointers with n gap*
   - *Follow-up: Single pass solution*

#### Stacks & Queues
**Easy:**
1. **Valid parentheses**
   - *Hint: Use stack for matching*
   - *Example: "()[]{}" → True*
   - *Follow-up: Handle different types*

2. **Implement queue using stacks**
   - *Hint: Use two stacks*
   - *Follow-up: Optimize for frequent operations*

**Medium:**
1. **Next greater element**
   - *Hint: Stack with indices*
   - *Example: [2,1,2,4,3,1] → [4,-1,4,-1,-1,-1]*
   - *Follow-up: Circular array version*

#### Trees
**Easy:**
1. **Maximum depth of binary tree**
   - *Hint: Recursive DFS*
   - *Follow-up: Iterative solution*

2. **Same tree**
   - *Hint: Recursive comparison*
   - *Follow-up: Iterative with stack*

**Medium:**
1. **Level order traversal**
   - *Hint: BFS with queue*
   - *Follow-up: Bottom-up traversal*

2. **Validate binary search tree**
   - *Hint: Inorder traversal or bounds checking*
   - *Follow-up: Handle duplicates*

**Hard:**
1. **Serialize and deserialize binary tree**
   - *Hint: Preorder traversal with markers*
   - *Follow-up: Space-optimal solution*

#### Graphs
**Medium:**
1. **Number of islands**
   - *Hint: DFS/BFS on 2D grid*
   - *Follow-up: Count islands of different sizes*

2. **Course schedule (detect cycle)**
   - *Hint: Topological sort or DFS with coloring*
   - *Follow-up: Return valid ordering*

**Hard:**
1. **Word ladder**
   - *Hint: BFS with word transformations*
   - *Follow-up: Find all shortest paths*

---

## System Design Questions

### Basic Concepts
1. **What is horizontal vs vertical scaling?**
   - Horizontal: Add more servers
   - Vertical: Increase server capacity

2. **Explain load balancing.**
   - Distribute incoming requests across multiple servers

3. **What is caching? Types of caching.**
   - Temporary storage for frequent data
   - Types: Browser, CDN, Application, Database

4. **Database sharding vs replication.**
   - Sharding: Horizontal partitioning
   - Replication: Data copying for availability

### System Design Problems
1. **Design a URL shortener (like bit.ly)**
2. **Design a chat application (like WhatsApp)**
3. **Design a social media feed (like Twitter)**
4. **Design a file storage system (like Dropbox)**
5. **Design a notification system**

---

## Behavioral Questions

### General Questions
1. **Tell me about yourself.**
2. **Why do you want to work here?**
3. **Where do you see yourself in 5 years?**
4. **What are your strengths and weaknesses?**

### Situation-Based Questions
1. **Tell me about a time you faced a challenging problem.**
   - *Use STAR method*

2. **Describe a situation where you had to work under pressure.**
   - *Focus on time management and results*

3. **Tell me about a time you disagreed with a team member.**
   - *Emphasize collaboration and resolution*

4. **Give an example of when you showed leadership.**
   - *Even without formal authority*

5. **Describe a time you failed and what you learned.**
   - *Show growth and learning mindset*

### Technical Behavioral Questions
1. **Tell me about a complex technical problem you solved.**
2. **How do you stay updated with new technologies?**
3. **Describe your approach to debugging.**
4. **How do you handle competing priorities?**
5. **Tell me about a time you had to learn a new technology quickly.**

---

## Preparation Tips

### For Resume Questions
- Prepare a 2-minute elevator pitch
- Have specific examples ready for each project
- Quantify achievements where possible

### For Technical Questions
- Start with brute force, then optimize
- Explain your thought process aloud
- Consider edge cases
- Test your solution with examples

### For Coding Questions
- Practice on platforms like LeetCode, HackerRank
- Focus on patterns rather than memorizing solutions
- Time yourself to improve speed
- Learn multiple approaches for each problem

### For System Design
- Think scalability from the beginning
- Consider trade-offs
- Start high-level, then dive into details
- Draw diagrams to visualize

### General Interview Tips
- Research the company thoroughly
- Prepare thoughtful questions to ask
- Practice mock interviews
- Get good sleep before the interview
- Arrive early and dress appropriately

---

## Recommended Study Schedule

### Week 1-2: Foundations
- Review CS fundamentals
- Practice easy coding problems
- Prepare resume talking points

### Week 3-4: Core DSA
- Medium coding problems
- Focus on arrays, strings, linked lists
- System design basics

### Week 5-6: Advanced Topics
- Hard coding problems
- Trees, graphs, dynamic programming
- Complex system design

### Week 7-8: Mock Interviews
- Full-length practice sessions
- Behavioral question practice
- Company-specific preparation

Good luck with your campus placements!