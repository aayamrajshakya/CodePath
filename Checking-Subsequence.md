*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How should the function handle empty strings for `s` and/or `t`?
  - If `s` is empty, the function should return True as an empty string is a subsequence of any string. If `t` is empty and `s` is not, the function should return False.
- What is the expected behavior if `s` is longer than `t`?
  - The function should return False, as a longer string cannot be a subsequence of a shorter one.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to traverse strings `s` and `t`. Increment the pointer for `s` only when characters match in both strings, but always increment the pointer for `t`.

```markdown
1) Initialize two pointers, `s_index` for string `s` and `t_index` for string `t`.
2) Traverse string `t` using the `t_index` pointer:
  a) If characters at both pointers match, increment the `s_index` pointer.
  b) Always increment the `t_index` pointer.
3) Check if `s_index` has reached the length of `s`, which means all characters of `s` were found in `t` in order.
4) Return True if the entire `s` is a subsequence of `t`, otherwise return False.
```

**⚠️ Common Mistakes**

- Forgetting to increment the `t_index` when characters do not match, which could lead to an infinite loop.
- Returning True prematurely without checking if all characters of `s` have been matched.

## I-mplement

```python
def is_subsequence_corrected(s, t):
    s_index, t_index = 0, 0
    while s_index < len(s) and t_index < len(t):
        if s[s_index] == t[t_index]:
            s_index += 1
        t_index += 1
    return s_index == len(s)
```