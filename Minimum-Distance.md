*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What if word1 and/or word2 are not in the list of words?
  - In those cases, we will return -1.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list of words and identify where word1 and word2 are located.

```markdown
1) Set an initial minimum distance to be the worst case (word1 and word2 are first and last in the list of words)
2) Loop through the list of words
  a) If the word is word1, record a start index
    i) If the end index has already been found, update the minimum distance (if smaller)
  b) Otherwise if the word is word2, record a stop index
    i) If the start index has already been foudn, update the minimum distance (if smaller)
3) If the minimum distance was at some point updated, return it
4) Otherwise, return -1
```

## I-mplement

```python
def min_distance(words, word1, word2):
    index1, index2 = -1, -1
    min_dist = len(words)  # Use the length of the list as the maximum possible distance
    for i, word in enumerate(words):
        if word == word1:
            index1 = i
            if index2 != -1:
                min_dist = min(min_dist, index1 - index2)
        elif word == word2:
            index2 = i
            if index1 != -1:
                min_dist = min(min_dist, index2 - index1)
    return min_dist if min_dist != len(words) else -1
```