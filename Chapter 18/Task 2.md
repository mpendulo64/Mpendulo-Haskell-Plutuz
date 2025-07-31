HC18T2: Create a Functor instance for the binary tree type Tree.
---


```haskell
-- Define a binary Tree type
data Tree a = Empty
            | Node a (Tree a) (Tree a)
            deriving (Show, Eq)

-- Functor instance for Tree
instance Functor Tree where
    fmap _ Empty = Empty
    fmap f (Node x left right) =
        Node (f x) (fmap f left) (fmap f right)

-- Example usage
main :: IO ()
main = do
    let tree = Node 5 (Node 3 Empty Empty) (Node 7 Empty Empty)
    putStrLn "🌳 Original Tree:"
    print tree

    let mappedTree = fmap (*2) tree
    putStrLn "\n🔁 Tree after applying (*2) to every value:"
    print mappedTree
```

---

### 🧠 Explanation

- **`Tree a`** is your recursive binary tree type.
  - `Empty` represents a leaf.
  - `Node x left right` wraps a value `x` and two subtrees.

- **`Functor` instance** enables:
  - `fmap f Empty` just returns `Empty`.
  - `fmap f (Node x left right)` applies `f` to the node value and recursively to its children.

- **Why Functor?**
  - You can easily transform a tree: for example, doubling all values or converting integers to strings — without rewriting traversal logic.



---

