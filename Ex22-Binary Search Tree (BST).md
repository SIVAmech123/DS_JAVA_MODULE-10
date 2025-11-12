# Ex22 Searching for a Book ID in a Binary Search Tree (BST)
## DATE:18/11/25
## AIM:
To design and implement a Python program that constructs a Binary Search Tree (BST) using given Book IDs and checks whether a specific Book ID exists in the BST.
## Algorithm
1. Start the program
2. Define a Node class to represent each node in the BST with attributes data, left, and right.
3. Define a function insert(root, key) to insert a new Book ID into the BST following BST rules:

If the BST is empty, create a new node.

If the key is smaller than the root’s data, insert it into the left subtree.

If the key is larger, insert it into the right subtree.
4.  Define a function search(root, key) to check whether a Book ID exists in the BST:

If the root is None, return False.

If the root’s data matches the key, return True.

Otherwise, recursively search in the left or right subtree depending on the value.
5.   In the main section:

Create an empty BST and insert a list of Book IDs into it.

Display the inserted Book IDs.

Prompt the user (or define in code) a Book ID to search for.

Use the search() function to determine if it exists.

Display the result.

Stop the program.

## Program:
```
"""
Program to construct a Binary Search Tree (BST) using given Book IDs 
and check whether a specific Book ID exists in the BST.
Developed by: K Dilli Babu
Register Number:  212224110015
"""

# Define a class for tree node
class Node:
    def __init__(self, data):
        self.data = data
        self.left = None
        self.right = None

# Function to insert a new node into the BST
def insert(root, key):
    if root is None:
        return Node(key)
    if key < root.data:
        root.left = insert(root.left, key)
    elif key > root.data:
        root.right = insert(root.right, key)
    return root

# Function to search for a Book ID in the BST
def search(root, key):
    if root is None:
        return False
    if root.data == key:
        return True
    elif key < root.data:
        return search(root.left, key)
    else:
        return search(root.right, key)

# Driver code
book_ids = [50, 30, 70, 20, 40, 60, 80]  # Example Book IDs
root = None

# Construct the BST
for id in book_ids:
    root = insert(root, id)

print("Book IDs in the library (BST):", book_ids)

# Search for a specific Book ID
search_id = 60
if search(root, search_id):
    print(f"Book ID {search_id} exists in the library system.")
else:
    print(f"Book ID {search_id} does not exist in the library system.")

```

## Output:

<img width="678" height="861" alt="image" src="https://github.com/user-attachments/assets/08a89472-808a-4959-9483-29c3f9eea320" />


## Result:
The program has been successfully implemented and executed.
It constructs a Binary Search Tree from the given Book IDs and accurately determines whether a queried Book ID exists in the library system.
