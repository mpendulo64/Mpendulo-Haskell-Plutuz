HC18T3: Define a function incrementTreeValues that adds one to every value in a tree using the Functor instance.
---


```haskell
-- Define the Tree type
data Tree a = Empty
            | Node a (Tree a) (Tree a)
            deriving (Show, Eq)

-- Functor instance for Tree
instance Functor Tree where
    fmap _ Empty = Empty
    fmap f (Node x left right) =
        Node (f x) (fmap f left) (fmap f right)

-- Function to increment every value in the tree
incrementTreeValues :: Num a => Tree a -> Tree a
incrementTreeValues = fmap (+1)

-- Example usage
main :: IO ()
main = do
    let tree = Node 10 (Node 5 Empty Empty) (Node 15 Empty Empty)
    putStrLn "🌳 Original Tree:"
    print tree

    let incrementedTree = incrementTreeValues tree
    putStrLn "\n🔼 Tree after incrementing each value:"
    print incrementedTree
```

---

### 🧠 Explanation

- **`Tree a`**: A binary tree holding values of type `a`.
- **`Functor` instance**: Enables `fmap` to apply a function to every value in the tree.
- **`incrementTreeValues`**:
  - Uses `fmap (+1)` to increment each value.
  - Works for any numeric type (`Num a =>`).
- **`main`**:
  - Builds a sample tree.
  - Applies the increment function.
  - Prints both original and updated trees.

---

