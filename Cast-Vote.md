*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Check if the candidate is already in the dictionary, add them if not, then increment their votes by 1.

```markdown
1) If the candidate is a key in the dict, increment the value by 1
2) Otherwise, map candidate -> 1 in the dict
```

## I-mplement

```python
def cast_vote(votes, candidate):
    if candidate in votes:
        votes[candidate] += 1
    else:
        votes[candidate] = 1
    return votes
``` 

*Alternative Solution*

```python
def cast_vote(votes, candidate):
    if candidate not in votes:
        votes[candidate] = 0
    votes[candidate] += 1
    return votes
``` 