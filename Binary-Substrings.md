*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Look for runs of consecutive numbers, and when two adjacent runs match in length, count that substring.

```markdown
1) Previous run length starts at 0
2) Current run length starts at 1
3) Count starts at 0
4) For each character except the first:
  a) Does current char match the prev char?
     i) If so, current run length goes up by 1
    ii) If not, current run is over:
        - Set prev run to curr run
        - Set curr run to 1
  b) Does prev run >= curr run?
     i) If so, add 1 to count 
5) Return count
```

**⚠️ Common Mistakes**

- Since you need to compare each character to the one before, be careful with your loop.  If you start at 0, your code might try to access index "-1" and run into an error.

## I-mplement

```python
def binary_substrings_count(s):
    prev_run_length = 0
    curr_run_length = 1
    count = 0
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            curr_run_length += 1
        else:
            prev_run_length = curr_run_length
            curr_run_length = 1
        if prev_run_length >= curr_run_length:
            count += 1
    return count
```