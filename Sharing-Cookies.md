*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should the function return if there are no cookies or no children?
  - The function should return 0, as no children can be made content without cookies.
- How does the function handle large numbers and potentially large inputs?
  - The function will work as long as it operates within Python's handling of large lists and sorts them efficiently.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Sort both the greed factors of the children and the sizes of the cookies. Then, attempt to satisfy each child's minimum greed factor with the smallest available cookie that meets or exceeds it.

```markdown
1) Sort the list of greed factors and the list of cookie sizes.
2) Initialize pointers for children (child_i) and cookies (cookie_j).
3) While there are still children and cookies:
  a) Check if the current smallest cookie can satisfy the current child's greed.
  b) If it can, move to the next child.
  c) Move to the next cookie regardless of whether it satisfied a child's greed or not.
4) Return the count of content children, indicated by the child index pointer.
```

**⚠️ Common Mistakes**

- Not sorting the greed factors and cookie sizes could lead to inefficiency and incorrect results.
- Failing to increment the cookie pointer when a cookie doesn't satisfy a child, leading to unnecessary comparisons.

## I-mplement

```python
def find_content_children(g, s):
    g.sort()  # Sort the greed factors
    s.sort()  # Sort the sizes of the cookies
    child_i, cookie_j = 0, 0
    while child_i < len(g) and cookie_j < len(s):
        if g[child_i] <= s[cookie_j]:
            # This child can be content with this cookie, move to next child
            child_i += 1
        # Move to next cookie whether it was used to content a child or not
        cookie_j += 1
    return child_i
```