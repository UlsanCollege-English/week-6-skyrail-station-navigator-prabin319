[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/mHMwxQwH)
# Weekly Coding #5: Skyrail Station Navigator

## Summary
This program implements a binary tree and binary search tree (BST) using a `TreeNode` class.
It supports three tree traversal methods — preorder, inorder, and postorder — each returning node values in a specific order.
It also implements BST search (`bst_contains`) to check if a value exists, and BST insertion (`bst_insert`) to add new values while maintaining BST ordering.
Duplicate values are ignored during insertion.

---

## Approach
- **Preorder traversal:** Recursively visit the current node first, then the left subtree, then the right subtree. Base case returns `[]` for `None`.
- **Inorder traversal:** Recursively visit the left subtree first, then the current node, then the right subtree. This produces sorted output for a valid BST.
- **Postorder traversal:** Recursively visit the left subtree, then the right subtree, then the current node last.
- **BST search:** At each node, return `True` if the value matches. Go left if the target is smaller, right if larger. Return `False` when `None` is reached.
- **BST insert:** Navigate left or right using BST ordering rules. When `None` is reached, create and return a new `TreeNode`. If the value already exists, return the node unchanged.

---

## Complexity

### `preorder_values`
- **Time:** O(n)
- **Space:** O(n)
- **Why:** Every node is visited exactly once. The output list and the recursion call stack together use O(n) space.

### `inorder_values`
- **Time:** O(n)
- **Space:** O(n)
- **Why:** Same as preorder — every node is visited once, and the stack depth equals the tree height (O(n) worst case for a skewed tree).

### `postorder_values`
- **Time:** O(n)
- **Space:** O(n)
- **Why:** Same reasoning as preorder and inorder.

### `bst_contains`
- **Time:** O(h) where h is the tree height; O(log n) for a balanced BST, O(n) worst case
- **Space:** O(h) for the recursion call stack
- **Why:** At each step we go left or right, cutting out half the tree if balanced. The call stack depth equals the path length to the target.

### `bst_insert`
- **Time:** O(h) — same as `bst_contains`
- **Space:** O(h) for the recursion call stack
- **Why:** We traverse from root to the correct insertion point, which takes at most h steps.

---

## Edge-Case Checklist
- [x] Empty tree traversal returns `[]` — all three traversals return `[]` immediately when `root is None`
- [x] Single-node traversal works correctly — returns a one-element list with just that node's value
- [x] `bst_contains` returns `False` for an empty tree — the `if root is None: return False` base case handles this
- [x] `bst_contains` returns `False` when the target is missing — recursion reaches `None` without finding the value
- [x] `bst_insert` creates a root when the tree is empty — `if root is None: return TreeNode(value)` handles this
- [x] `bst_insert` ignores duplicate values — the `elif value > root.value` condition skips equal values and returns the node unchanged
- [x] I tested at least one deeper insert case — inserting 55 into the sample BST correctly places it between 50 and 60

---

## Assistance & Sources
- **AI used? (Y/N):** Y
- **What AI helped with:** Implementing all five functions and explaining the recursive logic for traversals and BST operations
- **Other sources used:** None

---

## Test Results
Paste or summarize your `pytest -q` result here.