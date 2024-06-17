*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should my program do if the task dict is empty?
  - Return `None`.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Loop through the list of tasks, and find the key for the task with the highest priority.  Remove and return that task.

```markdown
1) If the task dict is empty, return None
2) Find the highest priority value from dict values
3) The highest task is None by default
4) For each task and priority in the dict
  a) If the priority is the highest value
     i) If highest task is still None, this task is our new highest
    ii) If this task < highest task, this task is our new highest
5) Remove the highest task from the list
6) Return the highest task
```

**⚠️ Common Mistakes**

- To alphabetize strings, Python allows you to use the `<` and `>` operators, just like you would with numbers.  Make sure you don't reverse them!

## I-mplement

```python
def get_highest_priority_task(tasks):
    if not tasks:
        return None
    highest_priority = max(tasks.values())
    highest_task = None
    for task, priority in tasks.items():
        if priority == highest_priority:
            if highest_task is None or task < highest_task:
                highest_task = task
    tasks.pop(highest_task)
    return highest_task
``