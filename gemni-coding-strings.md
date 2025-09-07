Coding Questions: Strings
This section contains coding problems focused on string manipulation, a common topic in technical interviews.
Easy
Question: Reverse a String.
Write a function that takes a string as input and returns the string reversed.
Example:
Input: "hello"
Output: "olleh"
Hint: In many languages, you can iterate through the string from end to start and build a new string. In Python, you can use slicing [::-1].
Follow-up: Can you do this in-place in a character array without using extra space (for the output string)?
Question: Check for Palindrome.
Write a function that checks if a given string is a palindrome (reads the same forwards and backwards). The check should be case-insensitive and ignore non-alphanumeric characters.
Example:
Input: "A man, a plan, a canal: Panama"
Output: true
Hint: First, clean the string by converting it to lowercase and removing all non-alphanumeric characters. Then, use a two-pointer approach. Have one pointer at the beginning and one at the end. Move them towards the center, comparing characters at each step.
Medium
Question: Valid Anagram.
Given two strings s and t, write a function to determine if t is an anagram of s. An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
Example:
Input: s = "anagram", t = "nagaram"
Output: true
Input: s = "rat", t = "car"
Output: false
Hint: The simplest approach is to sort both strings and check if they are equal. A more efficient approach is to use a hash map (or an array of size 26 for lowercase English letters) to count the frequency of characters in the first string. Then, iterate through the second string, decrementing the counts. If you ever encounter a character not in the map or its count is zero, it's not an anagram. Finally, check if all counts in the map are zero.
Follow-up: How would you handle Unicode characters? (A hash map would be better than a fixed-size array).
Question: Longest Substring Without Repeating Characters.
Given a string s, find the length of the longest substring without repeating characters.
Example:
Input: s = "abcabcbb"
Output: 3 (The answer is "abc")
Input: s = "pwwkew"
Output: 3 (The answer is "wke")
Hint: This is a classic sliding window problem. Use two pointers, left and right, to define the current window. Use a hash set or hash map to keep track of the characters currently in the window.
Expand the window by moving the right pointer.
If the character at s[right] is already in the set, a repeat is found.
Shrink the window from the left by moving the left pointer and removing s[left] from the set, until the repeating character is removed.
Keep track of the maximum window size (right - left + 1) seen so far.
Follow-up: What is the time and space complexity of your solution?
Difficult
Question: Minimum Window Substring.
Given two strings s and t, return the minimum window in s which will contain all the characters in t. If there is no such window in s that covers all characters in t, return the empty string "".
Example:
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"
Hint: This is another sliding window problem, but more complex.
First, create a hash map (t_map) of character frequencies for the string t.
Use two pointers, left and right, to define the window in s. Also, maintain a count of how many characters from t you need (needed_chars) and how many you currently have in your window (formed_chars).
Expand the window by moving right. If s[right] is a character in t_map, update its count in your window's frequency map (window_map). If the count in window_map now matches the count in t_map for that character, increment formed_chars.
Once formed_chars equals the number of unique characters in t, you have a valid window.
Now, try to shrink the window from the left to find the minimum possible size. While shrinking, if you remove a character that was needed, you'll need to decrement formed_chars and continue expanding the window again.
Keep track of the start and end indices of the smallest valid window found so far.
Question: Word Break.
Given a string s and a dictionary of strings wordDict, return true if s can be segmented into a space-separated sequence of one or more dictionary words. Note that the same word in the dictionary may be reused multiple times in the segmentation.
Example:
Input: s = "leetcode", wordDict = ["leet", "code"]
Output: true
Input: s = "applepenapple", wordDict = ["apple", "pen"]
Output: true
Input: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
Output: false
Hint: This is a dynamic programming problem. Let dp[i] be a boolean value indicating whether the substring s[0...i-1] can be segmented.
dp[0] is true (representing an empty string).
The recurrence relation is: dp[i] is true if there exists an index j (where 0 <= j < i) such that dp[j] is true AND the substring s[j...i-1] is in the wordDict.
Iterate from i = 1 to s.length(). For each i, iterate j from 0 to i-1 and check the condition. The final answer is dp[s.length()].
Follow-up: Can you return all possible segmentations instead of just true/false? (This would require backtracking or a modified DP approach).
