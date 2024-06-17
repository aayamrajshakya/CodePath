*[[Unit 2 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Create and fill a dictionary using two lists as the keys and values.

```markdown
1) Create an empty dictionary
2) For each index in the keys/values lists
  a) Get the key from the keys list at that index
  b) Get the value from the values list at that index
  c) Add the key:value pair to the new dictionary
3) Return the new dictionary
```

**⚠️ Common Mistakes**

- If you just loop through elements in either list, it gets tricky to make sure you are matching their indices.  Instead, try constructing your loop to iterate over each index.

## I-mplement

```python
def create_dictionary(keys, values):
	result_dict = {}
	for i in range(len(keys)):
        	result_dict[keys[i]] = values[i]
	return result_dict
```