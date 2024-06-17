*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should my program do if there are no grades in the report_card?
  - In this case, return a grade of 0.0

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Map each grade to a points total, then calculate the GPA (grade point average).

```markdown
1) Create a reference dictionary that maps letter grades to points
2) If the report card is empty, return 0.0 early (to prevent division by zero)
3) Total points starts at 0
4) For each course in the report card:
  a) Find the corresponding points for the letter grade
  b) Add those points to the total
5) Calculate the average using the total points and # of courses
6) Return the GPA
```

**⚠️ Common Mistakes**

- Be sure your code prevents accidental division by zero when the report_card is empty!

## I-mplement

```python
def report_card(report_card):
  # Mapping of letter grades to grade points
  grade_points = {"A": 4, "B": 3, "C": 2, "D": 1, "F": 0}
  
  # Check if the report_card dictionary is empty
  if not report_card:
      return 0.0
  
  total_points = 0
  
  # Calculate the total grade points
  for grade in report_card.values():
	  points = grade_points[grade]
	  total_points += points
  
  # Calculate the GPA
  gpa = total_points / len(report_card)
  
  return gpa
``` 