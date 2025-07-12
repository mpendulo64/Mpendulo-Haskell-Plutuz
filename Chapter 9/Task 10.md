HC9T10: Binary Search Tree Data Type
---


```haskell
-- Define a binary search tree type
data BST a = Empty
           | Node a (BST a) (BST a)
           deriving Show

-- Example BST with Int values
sampleTree :: BST Int
sampleTree =
    Node 10
        (Node 5
            (Node 2 Empty Empty)
            (Node 7 Empty Empty))
        (Node 15
            Empty
            (Node 20 Empty Empty))

-- Print the tree
main :: IO ()
main = print sampleTree
```

---

### 🧠 Explanation

- **`data BST a = Empty | Node a (BST a) (BST a)`**:
  - Defines a recursive binary search tree type.
  - `Empty` represents a leaf (null pointer in other languages).
  - `Node a left right` stores a value and two subtrees.
  - `a` is a type parameter so this works with any comparable type (`Int`, `String`, etc.).

- **`deriving Show`**:
  - Automatically gives you a printable version for debugging or basic output.

- **`sampleTree`**:
  - Represents a BST where:
    - `10` is the root.
    - `5` is on the left, with children `2` and `7`.
    - `15` is on the right, with a child `20`.

---

