*[[Unit 4 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- How do the two methods compare in terms of efficiency?
- What are the trade-offs between using additional space versus modifying in place?

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Compare the two-pointer method with an alternative that uses slicing to reverse the list.

```markdown
1) Two-pointer method:
   - Time Complexity: O(n), because each element is visited once.
   - Space Complexity: O(1), as it only swaps elements in place without using extra space.
2) Non-two-pointer method (slicing and copying back):
   - Time Complexity: O(n), because it involves creating a new list and then copying elements back.
   - Space Complexity: O(n), as it requires additional space for the reversed list.

```

**⚠️ Common Mistakes**

- Misunderstanding space complexity of the non-two-pointer method, thinking no extra space is used.
- Not accounting for the overhead of list slicing and copying.

## I-mplement

```python
# NON TWO POINTER
# Time complexity: O(n)
# Space complexity: O(n)
def reverse_list(lst):
    reversed_lst = lst[::-1] # O(n) extra space
    for i in range(len(lst)): # O(n) time
        lst[i] = reversed_lst[i]
        
# TWO POINTER
# Time complexity: O(n)
# Space complexity: O(1)
def reverse_list(lst):
    left = 0
    right = len(lst) - 1
    
    while left < right: # O(n/2) --> O(n)
        temp = lst[left]
        lst[left] = lst[right]
        lst[right] = temp
        
        left += 1
        right -= 1
    
    return lst
```

**Time and Space Complexity Evaluation**
- Better Time Complexity: Both methods have O(n) time complexity.
- Better Space Complexity: The two-pointer method has better space efficiency with O(1) space complexity compared to O(n) for the slicing method.
