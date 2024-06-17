*[[Unit 3 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- What is there is only one word in the sentence?
  - The function should return the original string.

## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Reverse a list of the input words and return the joined sentence.

```markdown
1) First, split the sentence into a list of words
2) Slice the entire list with a negated step parameter
3) Join the list of words back into a sentence
4) Return the reversed sentence
```

## I-mplement

```python
def reverse_sentence(sentence):
    words = sentence.split(' ')
    reversed_words = words[::-1]
    reversed_sentence = ' '.join(reversed_words)
    return reversed_sentence
```