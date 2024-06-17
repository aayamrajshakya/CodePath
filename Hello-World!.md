*[[Unit 1 Session 1]] (Click for link to problem statements)*

## U-nderstand
 
> **Understand** what the interviewer is asking for by using test cases and questions about the problem.

- Will I need all 3 provided lines of code?
  - Yes.
- Will one line be used more than once? 
  - No, each line will be used only once.
- Are the lines already properly indented?
  - No, you will need to determine the appropriate indentation for each line.
   
## P-lan

> **Plan** the solution with appropriate visualizations and pseudocode.

**General Idea:** Put the lines of code in order to write and call a function that prints a message.

```markdown
1) Create a new function by writing a function signature
2) Inside the function body, print "Hello World" to the console
3) Call the created function
```

**⚠️ Common Mistakes**

- Unlike some other coding languages, in Python, function calls must happen **after** the function is defined.

## I-mplement

```python
def hello_world(): # Function signature
	print("Hello world!") # Function body. Will print "Hello world!" to the console

hello_world() # Function call
```