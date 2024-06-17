*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 25 mins
* 🛠️ **Topics**: Hash Table, String
* 📺 **Non-TIP101 Version**: [[Group Anagrams]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- How should we handle the case of empty strings?
    - Group all empty strings together in a separate list.

```
HAPPY CASE
Input: strs = [""eat"", ""tea"", ""tan"", ""ate"", ""nat"", ""bat""]
Output: [[""eat"", ""tea"", ""ate""], [""tan"", ""nat""], [""bat""]]
Explanation: ""eat"", ""tea"", and ""ate"" are anagrams and form one group, ""tan"" and ""nat"" form another, and ""bat"" is on its own.

HAPPY CASE
Input: strs = [""abc"", ""bca"", ""cab"", ""xyz"", ""zyx""]
Output: [[""abc"", ""bca"", ""cab""], [""xyz"", ""zyx""]]
Explanation: ""abc"", ""bca"", and ""cab"" are anagrams and form one group, while ""xyz"" and ""zyx"" form another.

EDGE CASE
Input: strs = [""""]
Output: [[""""]]
Explanation: The only string is an empty string, which forms a group by itself.

EDGE CASE
Input: strs = [""a""]
Output: [[""a""]]
Explanation: The only string is ""a"", which forms a group by itself.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Hash Table problems, we want to consider the following approaches:

- Using a hash map to group words that are anagrams of each other by sorting the characters in the word and using the sorted word as the key.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use a hash map to group anagrams. The key is the sorted version of the word, and the value is a list of words that are anagrams.

```
1) Initialize an empty hash map (anagrams_dict).
2) Iterate over each word in the input list:
    a) Sort the characters of the word to form the key.
    b) If the key is already in the hash map, append the word to the list.
    c) If the key is not in the hash map, create a new entry with the key and the word as the first element in the list.
3) Initialize an empty list (answer).
4) Iterate over the values in the hash map and append each list of anagrams to the answer list.
5) Return the answer list.
```

**⚠️ Common Mistakes**

- Forgetting to sort the characters of the word correctly.
- Not handling empty strings properly.
- Mismanaging the keys in the hash map.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def group_anagrams(strs):
    anagrams_dict = {}

    for word in strs:
        word_as_list = [char for char in word]
        word_as_list.sort()
        key = tuple(word_as_list)
        if anagrams_dict.get(key):
            anagrams_dict[key].append(word)
        else:
            anagrams_dict[key] = [word]
    
    answer = []

    for key, value in anagrams_dict.items():
        answer.append(value)
    return answer
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with `strs = [""eat"", ""tea"", ""tan"", ""ate"", ""nat"", ""bat""]`
    - `anagrams_dict = {('a', 'e', 't'): ['eat'], ('a', 'e', 't'): ['eat', 'tea'], ...}`
    - `answer = [['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]`

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the number of strings and `K` represents the maximum length of a string in the list `strs`.

* **Time Complexity**: `O(N * K log K)` because we need to sort each string.
* **Space Complexity**: `O(N * K)` to store the grouped anagrams in the hash map.