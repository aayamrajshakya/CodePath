*[[Unit 3 Session 2]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What should my function return if the string is empty?
  - In this case, return an empty list.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** First, create a map of each element -> its latest index.  Then loop through the string, keeping track of the last appearance and current index.  When they match, add the partition.


```markdown
1) First, create a map of element -> latest index
2) Create an empty list, and set start and end to 0
3) For each index and char in the string:
  a) if last_index[char] is larger, update end
  b) if current index and end are equal
    i) add the partition to the list
   ii) move start to index+1
4) Return the partition list
```

## I-mplement

```python
def partition_labels(s):
    last_index = {}
    for idx, char in enumerate(s):
        last_index[char] = idx
        
    partitions = []
    start = 0
    end = 0

    for i, char in enumerate(s):
        end = max(end, last_index[char])
        if i == end:
            partitions.append(end - start + 1)
            start = i + 1

    return partitions
```