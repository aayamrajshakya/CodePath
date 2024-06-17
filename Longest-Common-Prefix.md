*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, find the shortest string in the list.  Then check each character of that string, and if something does not match the other strings, return everything before that.

```markdown
1) If the strings list is empty, return none
2) Find the smallest of the strings by comparing their lengths
3) Loop through the index and value of each char in smallest
  a) Loop through each other string
    i) If the other[index] does not match smallest[index],
       return smallest from 0 to index-1
4) If everything matched, return smallest
```

**⚠️ Common Mistakes**

- Looping through the "index and value of each char" may seem tricky, but using `enumerate` in Python makes it much easier.

## I-mplement

```python
def longestCommonPrefix(strs):
    if not strs:
        return ""
    shortest_str = strs[0]
    for s in strs:
        if len(s) < len(shortest_str):
            shortest_str = s
    for i, char in enumerate(shortest_str):
        for other in strs:
            if other[i] != char:
                return shortest_str[:i]
    return shortest_str
```