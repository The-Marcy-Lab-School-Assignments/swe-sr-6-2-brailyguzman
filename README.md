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

#### **Definition of a Tree**

A tree is a hierarchical data structure that consists of nodes connected by edges. According to MDN:

> _“A tree is a widely used abstract data type that simulates a hierarchical tree structure, with a root value and subtrees of children, represented as a set of linked nodes.”_

A tree typically contains the following key components:

- **Root**: The topmost node in the tree, serving as the starting point from which all other nodes descend.
- **Leaf**: A node with no children (i.e., it does not point to any other nodes). These are the terminal nodes of the tree.
- **Depth**: The number of edges from the root node to a given node.
- **Height**: The longest path (number of edges) from the root node to the deepest leaf node.

---

### **JavaScript Implementation of a Tree**

```js
class Tree {
  constructor(root = null, left = null, right = null) {
    this.root = root;
    this.left = left;
    this.right = right;
  }

  addLeft(value) {
    this.left = new Tree(value);
  }

  addRight(value) {
    this.right = new Tree(value);
  }
}

// Creating a tree
const myTree = new Tree(5);
myTree.addLeft(4);
myTree.addRight(3);
```

#### **Explanation of the Code**

In this implementation:

1. We define a `Tree` class that represents a node in the tree. The constructor initializes a node with a root value and optional left and right child nodes.
2. The `addLeft` and `addRight` methods create new nodes and attach them to the left or right child, respectively.
3. We instantiate a tree with a root value of `5`, then add `4` as the left child and `3` as the right child, forming the following structure:

```
       5
      / \
     4   3
```

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

  return arr.join("");
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

DFS is a tree traversal algorithm that explores as far down a branch as possible before backtracking. There are three common types of DFS traversal:

1. **Pre-Order (Root → Left → Right)**
2. **In-Order (Left → Root → Right)**
3. **Post-Order (Left → Right → Root)**

### **Example Tree**

```
    A
   / \
  B   C
 / \   \
D   E   F
```

### **Pre-Order Traversal (Root → Left → Right)**

```js
const preOrder = (root) => {
  if (root === null) return;
  console.log(root.val);
  preOrder(root.left);
  preOrder(root.right);
};
```

**Output:**  
`A B D E C F`

Pre-order traversal first processes the root, then recursively visits the left subtree, followed by the right subtree.

---

### **Post-Order Traversal (Left → Right → Root)**

```js
const postOrder = (root) => {
  if (root === null) return;
  postOrder(root.left);
  postOrder(root.right);
  console.log(root.val);
};
```

**Output:**  
`D E B F C A`

In post-order traversal, the left subtree is processed first, then the right subtree, and finally the root.

---

### **In-Order Traversal (Left → Root → Right)**

```js
const inOrder = (root) => {
  if (root === null) return;
  inOrder(root.left);
  console.log(root.val);
  inOrder(root.right);
};
```

**Output:**  
`D B E A C F`

In in-order traversal, the left subtree is visited first, then the root, followed by the right subtree. This approach is particularly useful for binary search trees as it outputs nodes in sorted order.

---

### **Conclusion**

The key difference between pre-order, in-order, and post-order traversals lies in the order in which nodes are visited. While pre-order prioritizes the root before exploring subtrees, post-order processes children before their parent, and in-order follows a left-root-right sequence, making it ideal for sorted output in binary search trees.
