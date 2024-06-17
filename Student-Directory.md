*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create a dictionary from a list of keys (student names) and generate a unique ID for each value.

```markdown
1) Create a new, empty dict
2) The current student ID starts at 1
3) For each student name:
  a) In the new dict, map name -> current ID
  b) Increment current ID by one
4) Return the new dict
```

## I-mplement

```python
def student_directory(student_names):
    student_dict = {}
    student_id = 1  # Start student IDs at 1
    for name in student_names:
        student_dict[name] = student_id
        student_id += 1
    return student_dict
``` 