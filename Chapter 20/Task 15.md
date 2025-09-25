HC20T15: treeSum with Custom Monad
Write a function treeSum that computes the sum of elements in a binary tree using a custom monad.

We'll define:

1. A **binary tree data type**.
2. A **custom monad** to accumulate a running sum while traversing the tree.
3. A function `treeSum` that uses this monad to compute the sum of all elements.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

-- Define a simple binary tree
data Tree a = Empty
            | Node a (Tree a) (Tree a)
            deriving Show

-- Define a custom monad that carries an accumulating sum
newtype SumM a = SumM { runSumM :: Int -> (a, Int) }

-- Functor instance
instance Functor SumM where
    fmap f (SumM g) = SumM $ \s ->
        let (a, s') = g s
        in (f a, s')

-- Applicative instance
instance Applicative SumM where
    pure x = SumM $ \s -> (x, s)
    (SumM f) <*> (SumM g) = SumM $ \s ->
        let (func, s1) = f s
            (x, s2)   = g s1
        in (func x, s2)

-- Monad instance
instance Monad SumM where
    return = pure
    (SumM g) >>= f = SumM $ \s ->
        let (a, s1)      = g s
            (SumM h)     = f a
        in h s1

-- Helper: add a number to the running sum
add :: Int -> SumM ()
add n = SumM $ \s -> ((), s + n)

-- Compute sum of elements in a tree
treeSum :: Tree Int -> SumM ()
treeSum Empty = return ()
treeSum (Node x left right) = do
    add x
    treeSum left
    treeSum right

-- Helper to run treeSum and extract the total sum
runTreeSum :: Tree Int -> Int
runTreeSum t = snd (runSumM (treeSum t) 0)

-- Example tree
exampleTree :: Tree Int
exampleTree = Node 10
                (Node 5 (Node 2 Empty Empty) (Node 3 Empty Empty))
                (Node 7 Empty (Node 1 Empty Empty))

main :: IO ()
main = do
    putStrLn "Computing sum of tree elements..."
    print $ runTreeSum exampleTree
```

---

### ✅ **Explanation**

1. **Binary Tree**

   ```haskell
   data Tree a = Empty | Node a (Tree a) (Tree a)
   ```

   Represents a simple binary tree.

2. **Custom Monad (`SumM`)**

   * Wraps a function `Int -> (a, Int)` where `Int` is our running sum.
   * Behaves like a `State Int` monad but custom-built.

3. **`add` Function**
   Updates the accumulated sum by adding `n`.

4. **`treeSum`**

   * Recursively traverses the tree.
   * Calls `add x` for each node value `x`.

5. **`runTreeSum`**

   * Runs `treeSum` with an initial sum of `0` and extracts the final result.

---



