*[[Unit 4 Session 2]] (Click for link to problem statements)*

## U-nderstand

> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What happens if one of the lists is empty?
  - If one of the lists is empty, the function should return an empty list as there can be no intersection.
- How should the function handle duplicate elements within the lists?
  - If both lists contain duplicates, the intersection should include duplicated elements only if they appear in both lists the same number of times they overlap.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Utilize two pointers to compare elements in two sorted lists. If the elements match, add to the result list and move both pointers. Otherwise, move the pointer pointing to the smaller element to try to match the next one.

```markdown
1) Initialize an empty list `result` to store the intersection.
2) Start with two pointers, `l1_index` for list1 and `l2_index` for list2, both set to the beginning of their respective lists.
3) While both pointers are within their list bounds:
  a) Compare the elements at both pointers.
  b) If the elements are the same, add the element to `result` and increment both pointers.
  c) If the element in list1 is less than the element in list2, increment the list1 pointer.
  d) Otherwise, increment the list2 pointer.
4) Return the `result` list containing the intersection.
```

**⚠️ Common Mistakes**

- Not correctly handling the comparison logic which could lead to missed intersections or incorrect increments of pointers.
- Overlooking edge cases where one list might finish processing before the other due to differences in size or element distribution.

## I-mplement

```python
def find_intersection(lst1, lst2):
    result = []
    l1_index, l2_index = 0, 0

    while l1_index < len(lst1) and l2_index < len(lst2):
        if lst1[l1_index] == lst2[l2_index]:
            result.append(lst1[l1_index])
            l1_index += 1
            l2_index += 1
        elif lst1[l1_index] < lst2[l2_index]:
            l1_index += 1
        else:
            l2_index += 1

    return result
```