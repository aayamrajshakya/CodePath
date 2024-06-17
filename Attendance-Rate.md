*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will the `attendance_list` ever be empty?
  - No.  You can assume there is always at least one student.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Count how many students are present, then use that value to calculate the percentage.

```markdown
1) At first, our present student count is zero
2) Loop through the values in the attendance dict
  a) If the value is "present", add to present count
3) Find the total number of students
4) Divide the present count by the total student count 
5) Return the result as a percentage (multiplied by 100)
```

## I-mplement

```python
def attendance_rate(attendance_list):	
	present_students = 0
	
	for status in attendance_list.values():
		if status == "Present":
			present_students += 1
			
	num_students = len(attendance_list)
	
	return (present_students/num_students) * 100
``` 