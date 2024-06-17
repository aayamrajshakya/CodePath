*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will records always be a valid dictionary?
  - Yes, but it may or may not be empty!

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if an item is in the dict, update if so, and otherwise print a customized error message.

```markdown
1) Check if the key is in the dictionary
2) If so, set the dict at key -> new value
3) Otherwise, print the name of the item and "not found!"
```

**⚠️ Common Mistakes**

- When printing your error message, be sure to print the actual name of the item provided, not the literal string "<item>".

## I-mplement

```python
def update_or_warn(records, item, update_value):
    if item in records:
        records[item] = update_value
    else:
        print(item + " not found!")
``` 