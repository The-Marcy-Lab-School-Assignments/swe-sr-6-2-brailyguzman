# Technical Writing Assignment

For guidance on setting up and submitting this assignment, refer to the Marcy lab School Docs How-To guide for [Working with Short Response and Coding Assignments](https://marcylabschool.gitbook.io/marcy-lab-school-docs/fullstack-curriculum/how-tos/working-with-assignments#how-to-work-on-assignments).

## Prompt 1

Imagine you are giving a brief lesson on Recursion to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of recursion (feel free to quote an official source like MDN)
- An example in code.
- An explanation of the code example.
- An explanation of the kinds of functions that are best solved using recursion.

### Response 1

Recursion is:

> The act of a function calling itself, recursion is used to solve problems that contain smaller sub-problems. A recursive function can receive two inputs: a base case (ends recursion) or a recursive case (resumes recursion). -[MDN](https://developer.mozilla.org/en-US/docs/Glossary/Recursion)

Code Example:

```js
const reverse = (str) => {
  if (str.length === 0) {
    return str;
  }

  return str[str.length - 1] + reverse(str.slice(0, str.length - 1));
};
```

In the code above:

1. We check if an empty string was provided, if so we return the string back.
2. We recursively get the last character of the string on each recursive function call which at the ends gives you the reversed string.

Some functions that are best solved with recursion:

1. **Divide and Conquer Algorithms**:

- Examples: Merge Sort, Quick Sort, Binary Search
- These algorithms split a problem into smaller instances, solve them recursively, and then combine the results.

2. **Tree and Graph Traversals**

- Examples: Depth-First Search (DFS), Pre-order, Inorder,and Post-order Tree Traversal.
- Recursive functions make it easy to navigate hierarchial structures.

## Prompt 2

Imagine you are giving a brief lesson on the Tree data structure to a relatively new programmer. In your lesson make sure to include the following:

- A formal definition of a Tree (feel free to quote an official source like MDN)
- Definitions for key terms like **root**, **leaf**, **depth**, and **height** as they relate to Trees
- An example in code.
- An explanation of the code example.

### Response 2

## Prompt 3

Any iterative function can be written recursively. Provide an example of an iterative function and the same function written recursively. Then, explain the benefits and/or drawbacks of each approach.

### Response 3

For this example, I will be using be using the reverse a string function.

Iterative:

```js
const reverse = (str) => {
  const arr = [];

  for (let i = str.length - 1; i >= 0; i--) {
    console.log(str[i]);
    arr.push(str[i]);
  }

  return arr.join('');
};
```

Recursively:

```js
const reverse = (str) => {
  if (str.length === 0) {
    return str;
  }

  return str[str.length - 1] + reverse(str.slice(0, str.length - 1));
};
```

### Comparison

Both ways achieve the same goal of reversing a string, but they do so using different techniques.

**Iterative Approach**:

- Uses a `for` loop to iterate through the string backwards.
- Stores characters in an array then joins them together.
- **Pros**:
  - More memory-efficient as it avoids extensive function calls (recursion)
  - Faster because it doesn't rely on the call stack.
- **Cons**:
  - Requires looping, which can be less intuitive in some cases.

**Recursive Approach**:

- Calls itself on progressing smaller substrings
- Uses stack memory to track function calls
- **Pros**:
  - More elegant and readable for problems that fit a recursive structure.
  - Can simplify complex problems like tree traversal.
- **Cons**:
  - Uses more memory due to recursive calls (each function call is stored in the call stack).
  - May cause stack overflow for larger inputs.

**When to use which**:

- Use **Iteration** when performance and memory efficiency is a priority.
- Use **Recursion** when working on problems that involve being broken down into smaller sub-problems. (e.g., tree traversal, backtracking problems).

## Prompt 4

Depth-first-search is an algorithm of traversing through a tree that explores as far as possible along a single branch before backtracking and exploring other branches. The three approaches for depth-first-search are "inorder", "preorder", and "postorder".

Using this tree as an example, explain the differences between these three approaches, providing implementations of each (recursive or iterative, its up to you but one of them is definitely cleaner).

```
    A
   / \
  B   C
 / \   \
D   E   F
```

### Response 4
