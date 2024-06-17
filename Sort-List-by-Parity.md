*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should happen if the list is completely sorted according to the parity rule?
  - If the list is already sorted where all even indices hold even numbers and odd indices hold odd numbers, the function should return the list as it is.
- How does the function handle an empty list?
  - The function should return an empty list, as there are no elements to sort or rearrange.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers to separately track the positions where even and odd numbers should be placed. Swap elements that are out of place.

```markdown
1) Initialize two pointers, `evenPointer` starting at index 0 and `oddPointer` starting at index 1.
2) Iterate through the list:
  a) Move the `evenPointer` to the next even-indexed position where there's an odd number.
  b) Move the `oddPointer` to the next odd-indexed position where there's an even number.
3) If both pointers find elements that are out of place and within the bounds of the list, swap these elements.
4) Continue the process until one or both pointers exceed the bounds of the list.
5) Return the rearranged list.
```

**⚠️ Common Mistakes**

- Not correctly maintaining the step size of the pointers, which should increment by 2, not 1.
- Performing swaps when one or both pointers are out of bounds, leading to potential errors or inefficiencies.

## I-mplement

```python
def sort_array_by_parity(nums):
	  n = len(nums)
    evenPointer, oddPointer = 0, 1  # Starting indices for even and odd
    
    while evenPointer < n and oddPointer < n:
        # Find the next even number that is out of place
        while evenPointer < n and nums[evenPointer] % 2 == 0:
            evenPointer += 2
        # Find the next odd number that is out of place
        while oddPointer < n and nums[oddPointer] % 2 == 1:
            oddPointer += 2
        
        # If neither pointer has reached the end, swap their elements
        if evenPointer < n and oddPointer < n:
            temp = nums[evenPointer]   
            nums[evenPointer] = nums[oddPointer]
            nums[oddPointer] = temp
    
    return nums
```