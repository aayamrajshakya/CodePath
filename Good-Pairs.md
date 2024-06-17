*[[Unit 2 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Why does the `i < j` thing matter?
  - It prevents you from counting the same pair twice! 

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, find out how many of each element are in the list.  Then calculate how many possible pairs can exist for each value, and add these up.

```markdown
1) First, create a frequency map for the list¹
2) Create a variable to hold pairs, initialized to 0
3) For each value in our frequency map:
  a) Calculate the possible pairs for that value
  b) Add the possible pairs to our pairs variable
4) Return the total number of pairs
```
*¹ see [[Frequency Count]] for psuedocode*

**⚠️ Common Mistakes**

- You will need to use a Combination Formula for this problem.  If you're not brushed up on statistics, try looking up "n choose 2 formula". 


## I-mplement

```python
def numIdenticalPairs(nums):
    # Frequency map to count occurrences of each number
    frequency_map = {}
    for num in nums:
        if num in frequency_map:
            frequency_map[num] += 1
        else:
            frequency_map[num] = 1
            
    # Count the number of good pairs
    good_pairs = 0
    for count in frequency_map.values():
        good_pairs += count * (count - 1) // 2  # Combination of 2 from n
        
    return good_pairs
```
