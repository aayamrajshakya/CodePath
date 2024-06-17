*[[Unit 10 Session 1]] (Click for link to problem statements)*

## Problem Highlights

* 💡 **Difficulty:** Medium
* ⏰ **Time to complete**: 30 mins
* 🛠️ **Topics**: Two Pointers, Array
* 📺 **Non-TIP101 Version**: [[Container with Most Water]]
    
## 1: U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.
> - Established a set (2-3) of test cases to verify their own solution later.
> - Established a set (1-2) of edge cases to verify their solution handles complexities.
> - Have fully understood the problem and have no clarifying questions.
> - Have you verified any Time/Space Constraints for this problem?

- What should be returned if the array is empty or has only one element?
    - 0, since no container can be formed.

```
HAPPY CASE
Input: height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
Output: 49
Explanation: The lines at index 1 and index 8 form a container with maximum area = 49.

HAPPY CASE
Input: height = [1, 1]
Output: 1
Explanation: The lines at index 0 and index 1 form a container with area = 1.

EDGE CASE
Input: height = []
Output: 0
Explanation: No container can be formed with an empty array.

EDGE CASE
Input: height = [1]
Output: 0
Explanation: No container can be formed with a single element.
```
    
## 2: M-atch

> **Match** what this problem looks like to known categories of problems, e.g. Linked List or Dynamic Programming, and strategies or patterns in those categories.

For Array and Two Pointer problems, we want to consider the following approaches:

- Using two pointers to iterate from both ends of the array towards the center to find the maximum area.
- Calculating the area formed by the lines at the two pointers and updating the maximum area accordingly.

## 3: P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Use two pointers, one starting from the beginning and one from the end of the array. Calculate the area formed by the lines at the two pointers and update the maximum area if the current area is larger. Move the pointer pointing to the shorter line towards the center.

```
1) Initialize two pointers, left and right, to the start and end of the array respectively.
2) Initialize max_water to 0 to keep track of the maximum area found.
3) While left is less than right:
    a) Calculate the width between the two pointers.
    b) Calculate the current area formed by the lines at the two pointers.
    c) Update max_water if the current area is larger.
    d) Move the pointer pointing to the shorter line towards the center.
4) Return max_water.
```

**⚠️ Common Mistakes**

- Not correctly updating the pointers after calculating the area.
- Not handling edge cases where the array is empty or has only one element.

## 4: I-mplement

> **Implement** the code to solve the algorithm.

```
def max_area(height):
    left = 0
    right = len(height) - 1
    max_water = 0

    while left < right:
        # Calculate the current area
        width = right - left
        current_height = min(height[left], height[right])
        current_area = width * current_height

        # Update the maximum area if the current one is larger
        max_water = max(max_water, current_area)

        # Move the pointer pointing to the shorter line
        if height[left] < height[right]:
            left += 1
        else:
            right -= 1

    return max_water
```
 
## 5: R-eview

> **Review** the code by running specific example(s) and recording values (watchlist) of your code's variables along the way.

- Trace through your code with an input to check for the expected output.
- Example: Trace with height = [1, 8, 6, 2, 5, 4, 8, 3, 7]
    - left = 0, right = 8, current_area = 49
    - max_water updated to 49
    - Move right pointer to 7, continue
    - Continue until left and right pointers meet

## 6: E-valuate

> **Evaluate** the performance of your algorithm and state any strong/weak or future potential work.

Assume `N` represents the length of the array `height`.

* **Time Complexity**: `O(N)` because we need to traverse the array once with two pointers.
* **Space Complexity**: `O(1)` because we only use a constant amount of extra space.