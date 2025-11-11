# Ex21 Count the Number of Nodes in the Left Subtree of a Binary Tree
## DATE:
## AIM:
To design and implement a Python program that constructs a binary tree from given level order input and counts the number of nodes present in the left subtree of the root node

## Algorithm
1. Start the program
2. Define a class Node to represent each node in the binary tree
3. Create a function insertLevelOrder(arr, root, i, n) to construct the binary tree from a given level order list.
4. Define a function countNodes(root) that returns the total number of nodes in a given subtree.
5.  Read or define the level order input array representing the binary tree.
6.  Construct the binary tree using the insertLevelOrder() function.
7.  Identify the left child of the root and call countNodes() on it.
8.  Display the number of nodes in the left subtree.
9.   Stop the program.

## Program:
```
"""
Program to construct a binary tree from given level order input and count the number of nodes 
in the left subtree of the root node.
Developed by: K Dilli babu
Register Number:  212224110015
"""

# Define a Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

# Function to insert nodes in level order
def insertLevelOrder(arr, root, i, n):
    if i < n:
        temp = Node(arr[i])
        root = temp

        # Insert left child
        root.left = insertLevelOrder(arr, root.left, 2 * i + 1, n)

        # Insert right child
        root.right = insertLevelOrder(arr, root.right, 2 * i + 2, n)
    return root

# Function to count nodes in a subtree
def countNodes(root):
    if root is None:
        return 0
    return 1 + countNodes(root.left) + countNodes(root.right)

# Driver Code
arr = [1, 2, 3, 4, 5, 6, 7]  # Level order input
n = len(arr)
root = insertLevelOrder(arr, None, 0, n)

# Count nodes in the left subtree of the root
if root.left:
    left_count = countNodes(root.left)
    print("Number of nodes in the left subtree:", left_count)
else:
    print("No left subtree exists.")

```

## Output:

<img width="794" height="962" alt="image" src="https://github.com/user-attachments/assets/9a0f85e9-85cd-46e9-a3b0-61858b5cddfc" />


## Result:
The program has been successfully implemented and executed.
It correctly constructs the binary tree from level order input and counts the number of nodes in the left subtree of the root node.
