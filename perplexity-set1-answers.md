# Comprehensive Campus Placement Question Bank with Answers

## 1. Resume & Project Questions

### Sample Question: Tell me about yourself.
#### Sample Answer:
"I am a final year Computer Engineering student with a passion for building scalable software solutions. I have interned at XYZ Corp where I worked on a large-scale e-commerce application, improving its search efficiency by 30%. My core strengths include Java, Python, and React, and I'm keen to join an innovative tech company to apply my skills."

### Sample Question: Describe your favorite project in detail.
#### Sample Answer:
"During my third year, I led a team project to build a campus event management app. I designed the backend using Node.js and MongoDB, implemented authentication, and optimized queries to reduce latency by 40%. The project taught me end-to-end application development and teamwork."

---

## 2. Computer Engineering Theory Questions (with answers)

### Q: What is the difference between process and thread?
**A:**
- Process: An independent execution unit with its own memory space.
- Thread: A lightweight unit of process sharing the same memory, allowing parallel execution within a process.

### Q: Explain TCP vs UDP.
**A:**
- TCP: Connection-oriented, reliable, ensures ordered delivery (useful for applications like HTTP, FTP).
- UDP: Connectionless, faster, no guarantee of delivery or order (used in streaming/gaming).

### Q: What is normalization in databases?
**A:**
Normalization organizes data to reduce redundancy. Normal forms (1NF, 2NF, 3NF) each resolve increasingly complex redundancy and dependency issues.

---

## 3. AI / LLM Questions with Answers

### Q: What is Artificial Intelligence?
**A:** AI lets machines perform tasks that typically require human intelligence. Examples are chatbots, autonomous vehicles, and recommendation systems.

### Q: What is a Large Language Model (LLM)?
**A:** An LLM is an advanced machine learning model trained on massive text data. It can generate and understand human language (e.g., GPT-4, BERT).

### Q: How does the attention mechanism work in transformers?
**A:** The attention mechanism assigns weights to input tokens, allowing the model to focus on relevant context when generating predictions. This greatly improves performance in tasks like translation.

---

## 4. Coding Questions (with answers, hints, follow-ups, examples)

### Category: String

#### Q: Easy: Reverse a string
**Example:** "hello" → "olleh"
**Hint:** Two pointers or slicing.
**Answer:**
```python
def reverse_string(s):
    return s[::-1]
```
**Follow-up:** Try using a loop/in-place swap.

#### Q: Medium: Longest substring without repeating characters
**Example:** "abcabcbb" → 3
**Hint:** Sliding window technique; store last-seen indices in a hashmap.
**Answer:**
```python
def lengthOfLongestSubstring(s):
   char_map = {}
   left = max_length = 0
   for right, char in enumerate(s):
       if char in char_map and char_map[char] >= left:
           left = char_map[char] + 1
       char_map[char] = right
       max_length = max(max_length, right - left + 1)
   return max_length
```
**Follow-up:** Print the actual substring.

#### Q: Hard: Minimum window substring
**Example:** s='ADOBECODEBANC', t='ABC' → 'BANC'
**Hint:** Use a sliding window and count the characters needed.
**Answer:**
```python
def minWindow(s, t):
    from collections import Counter
    need = Counter(t)
    missing = len(t)
    left = start = end = 0
    for right, char in enumerate(s, 1):
        if need[char] > 0:
            missing -= 1
        need[char] -= 1
        if missing == 0:
            while left < right and need[s[left]] < 0:
                need[s[left]] += 1
                left += 1
            if not end or right - left < end - start:
                start, end = left, right
            need[s[left]] += 1
            missing += 1
            left += 1
    return s[start:end]
```
**Follow-up:** What if case-insensitive?

### Category: Hash Map

#### Q: Easy: Two sum
**Example:** [2,7,11,15], target=9 → [0,1]
**Hint:** Store map of {num: index}; check if (target - num) is in map.
**Answer:**
```python
def twoSum(nums, target):
   num_map = {}
   for i, num in enumerate(nums):
       if (target - num) in num_map:
           return [num_map[target - num], i]
       num_map[num] = i
```
**Follow-up:** Multiple pairs? Return all pairs.

#### Q: Medium: Subarray sum equals K
**Example:** [1,2,3], K=3 → 2
**Hint:** Use prefix sum and a hashmap to count all sums seen so far.
**Answer:**
```python
def subarraySum(nums, k):
    from collections import defaultdict
    count = 0
    curr_sum = 0
    sum_map = defaultdict(int)
    sum_map[0] = 1
    for num in nums:
        curr_sum += num
        count += sum_map[curr_sum - k]
        sum_map[curr_sum] += 1
    return count
```
**Follow-up:** Handle negative numbers.

---

## 5. System Design Questions (sample with brief answers)

### Q: What is horizontal vs vertical scaling?
**A:**
- Horizontal scaling: Add more machines to handle increased load.
- Vertical scaling: Increase power of existing servers (CPU/memory).

### Q: How would you design a URL shortener?
**A:**
1. **Requirement Gathering:** Unique short code for long URLs, redirection, analytics, and handling large scale.
2. **High-level Design:**
   - API: POST to create, GET to redirect.
   - Storage: Use hash or counter for unique code; key-value database for mapping.
   - Redundancy and caching for performance.
   - Use DNS, request queue, and rate limiting for scaling.

---

## 6. Behavioral Questions (answers use STAR method)

### Q: Tell me about a time you led a team.
**A:** "During my internship, I was made the lead of a 4-member team to deliver a reporting dashboard. I delegated tasks, scheduled regular check-ins, and ensured clear communication. Despite a tight deadline, we successfully launched the dashboard on-time."

---

*You can expand each section with more questions and detailed answers as needed for your preparation.*

Good luck!