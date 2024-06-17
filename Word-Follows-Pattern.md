*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the patterns always be only "a" and "b"? 
  - No.  Your solution should work for any pattern string.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a map of pattern letters -> words, and if there is ever an inconsistency, return False.

```markdown
1) Split the input string into a list of words
2) If the # of words is different from pattern length, return False
3) Create an empty dict for the pattern map
4) For each index, word in the words list
  a) Get the pattern char at that index
  b) Is the char already in the map?
    i) If not, add char -> word to map
   ii) Otherwise, if map[char] != word, return False
5) If we go through all words and don't break the
   pattern, return True
```

## I-mplement

```python
def wordPattern(pattern, s):
    words = s.split()
    if len(pattern) != len(words):
        return False
    
    pattern_map = {}
    for index, word in enumerate(words):
        p_char = pattern[index]
        # Did we already use this char for another word?
        if p_char not in pattern_map:
            pattern_map[p_char] = word
        elif pattern_map[p_char] != word:
            return False

    # We couldn't find any mis-matches
    return True
```