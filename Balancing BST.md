Status: #

Class: [[CSX3003]]

Subject/Topics: #DSA

Date: 2024-09-23

Teacher:
___
#Name - Puran Paodensakul
#ID - 6611140
#Sec - 542
Notes:
To balance an uneven Binary Search Tree (BST) with nodes `1, 2, 3, 4, 5, 6, 7`, you can convert it into a balanced tree by finding the middle element of the sequence and reorganizing the tree structure.

Here’s how to balance the tree step-by-step:

### 1. Initial sequence (already sorted):
```
1, 2, 3, 4, 5, 6, 7
```

### 2. Identify the middle element:
- The middle element is **4** (this will be the root of the balanced tree).

### 3. Split the sequence:
- Left of **4**: `1, 2, 3`
- Right of **4**: `5, 6, 7`

### 4. Recursively pick the middle elements of the left and right sub-arrays:
- For the left half `1, 2, 3`:
  - Middle element: **2**
  - Left of **2**: **1**
  - Right of **2**: **3**
- For the right half `5, 6, 7`:
  - Middle element: **6**
  - Left of **6**: **5**
  - Right of **6**: **7**

### 5. Final balanced Binary Search Tree:
```
        4
      /   \
    2       6
   / \     / \
  1   3   5   7
```

### Key Steps for Balancing an Uneven Tree:
1. Find the middle of the sorted sequence (which gives you the root).
2. Recursively apply the same process to the left and right sub-arrays to maintain balance in the subtrees.
3. Insert the nodes in this order to build the balanced tree.

### General Method:
If you have an uneven tree, you can:
1. **Traverse** the tree in-order to get a sorted sequence of elements.
2. **Rebuild** the tree by recursively selecting the middle element from the sorted sequence and inserting it as the root, while balancing left and right subtrees.

This method ensures that the tree remains balanced with minimal height.


When you have an **even number** of elements like `1, 2, 3, 4, 5, 6, 7, 8`, the process of balancing is similar to that for an odd number, but you have to choose one of the two middle elements as the root.

For **even numbers**, there are two middle elements, and you can choose either. Let's go step-by-step using the sequence `1, 2, 3, 4, 5, 6, 7, 8`:

### 1. Initial sequence:
```
1, 2, 3, 4, 5, 6, 7, 8
```

### 2. Choose the middle element:
Since there are two middle elements (`4` and `5`), you can choose either as the root.

Let’s pick **5** as the root.

### 3. Split the sequence:
- Left half: `1, 2, 3, 4`
- Right half: `6, 7, 8`

### 4. Apply the same process recursively to the left and right sub-arrays:
- **Left half `1, 2, 3, 4`**:
  - Middle element: **2**
  - Left of **2**: **1**
  - Right of **2**: `3, 4`
    - Middle element: **3**
    - Right of **3**: **4**
    
- **Right half `6, 7, 8`**:
  - Middle element: **7**
  - Left of **7**: **6**
  - Right of **7**: **8**

### 5. Final balanced Binary Search Tree (choosing **5** as the root):
```
         5
       /   \
     2       7
    / \     / \
   1   3   6   8
        \
         4
```

### Alternatively, if you choose **4** as the root:

#### 1. Choose **4** as the root:
- Left half: `1, 2, 3`
- Right half: `5, 6, 7, 8`

#### 2. Split and apply recursively:
- **Left half `1, 2, 3`**:
  - Middle element: **2**
  - Left of **2**: **1**
  - Right of **2**: **3**
  
- **Right half `5, 6, 7, 8`**:
  - Middle element: **6**
  - Left of **6**: **5**
  - Right of **6**: `7, 8`
    - Middle element: **7**
    - Right of **7**: **8**

#### 3. Final balanced Binary Search Tree (choosing **4** as the root):
```
         4
       /   \
     2       6
    / \     / \
   1   3   5   7
               \
                8
```

### Key Points:
- You can choose either middle element in an even sequence.
- The final tree may look slightly different depending on which middle element you choose, but both versions will be balanced.
- The process involves finding the middle of each sub-array and recursively building left and right subtrees to maintain balance.

### Rearranged sequences:
- If you choose **5** as the root: `5, 2, 1, 3, 4, 7, 6, 8`
- If you choose **4** as the root: `4, 2, 1, 3, 6, 5, 7, 8`


