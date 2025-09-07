```markdown
# Coding Questions: Strings

This section contains coding problems focused on **string manipulation**, a common topic in technical interviews.

---

## **Table of Contents**
- [Easy](#easy)
  - [Reverse a String](#question-reverse-a-string)
  - [Check for Palindrome](#question-check-for-palindrome)
- [Medium](#medium)
  - [Valid Anagram](#question-valid-anagram)
  - [Longest Substring Without Repeating Characters](#question-longest-substring-without-repeating-characters)
- [Difficult](#difficult)
  - [Minimum Window Substring](#question-minimum-window-substring)
  - [Word Break](#question-word-break)

---

## **Easy**

### **Question:** Reverse a String  
Write a function that takes a string as input and returns the string reversed.

**Example:**  
```

Input: "hello"
Output: "olleh"

```

**Hint:**  
In many languages, you can iterate through the string from end to start and build a new string.  
In **Python**, you can use slicing `[::-1]`.

**Follow-up:**  
Can you do this **in-place** in a character array **without using extra space**?

---

### **Question:** Check for Palindrome  
Write a function that checks if a given string is a **palindrome** (reads the same forwards and backwards).  
The check should be **case-insensitive** and **ignore non-alphanumeric characters**.

**Example:**  
```

Input: "A man, a plan, a canal: Panama"
Output: true

```

**Hint:**  
1. Convert to lowercase.  
2. Remove all non-alphanumeric characters.  
3. Use a **two-pointer approach**:  
   - One pointer at start, one at end.  
   - Compare and move inward.  

---

## **Medium**

### **Question:** Valid Anagram  
Given two strings `s` and `t`, write a function to determine if `t` is an **anagram** of `s`.

**Examples:**  
```

Input: s = "anagram", t = "nagaram"
Output: true

Input: s = "rat", t = "car"
Output: false

```

**Hint:**  
- Simple: Sort both strings and compare.  
- Efficient:  
  - Use **hash map** or an **array of size 26** to count character frequencies.  
  - Iterate through `t` and decrement counts.  

**Follow-up:**  
How would you handle **Unicode characters**? (Hash map is better than a fixed array).

---

### **Question:** Longest Substring Without Repeating Characters  
Given a string `s`, find the **length of the longest substring without repeating characters**.

**Examples:**  
```

Input: s = "abcabcbb"
Output: 3 ("abc")

Input: s = "pwwkew"
Output: 3 ("wke")

```

**Hint:**  
- **Sliding Window** + HashSet/HashMap:  
  - Use two pointers (`left`, `right`).  
  - Expand `right`, check for duplicates.  
  - If duplicate, move `left` until duplicate is removed.  
  - Track `max_length`.  

**Follow-up:**  
What is the **time and space complexity**?

---

## **Difficult**

### **Question:** Minimum Window Substring  
Given two strings `s` and `t`, return the **minimum window in `s`** which will contain **all characters in `t`**.  
If no such window exists, return `""`.

**Example:**  
```

Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"

```

**Hint:**  
- **Sliding Window with Hash Maps**:  
  1. Build `t_map` for frequency of `t`.  
  2. Move `right` to expand window, update `window_map`.  
  3. When all characters matched, shrink from `left`.  
  4. Track smallest valid window.  

---

### **Question:** Word Break  
Given a string `s` and a dictionary `wordDict`, return **true** if `s` can be segmented into a **space-separated sequence of one or more dictionary words**.

**Examples:**  
```

Input: s = "leetcode", wordDict = \["leet", "code"]
Output: true

Input: s = "applepenapple", wordDict = \["apple", "pen"]
Output: true

Input: s = "catsandog", wordDict = \["cats", "dog", "sand", "and", "cat"]
Output: false

```

**Hint:**  
- **Dynamic Programming**:  
  - `dp[i]` = true if `s[0...i-1]` can be segmented.  
  - `dp[0] = true` (empty string).  
  - For each `i`, check all `j < i` if `dp[j]` is true and `s[j...i-1]` in `wordDict`.  

**Follow-up:**  
Can you return **all possible segmentations** instead of just true/false? (Requires **backtracking or modified DP**).

