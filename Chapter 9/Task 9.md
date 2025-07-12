HC9T9: Check for Element in a Sequence
---



```haskell
-- Define the custom recursive Sequence type
data Sequence a = End | Node a (Sequence a)
    deriving Show

-- Check if an element exists in a Sequence
elemSeq :: Eq a => a -> Sequence a -> Bool
elemSeq _ End = False
elemSeq x (Node y next)
    | x == y    = True
    | otherwise = elemSeq x next

-- Example usage
main :: IO ()
main = do
    let seq1 = Node 1 (Node 2 (Node 3 End))
    print $ elemSeq 2 seq1   -- Output: True
    print $ elemSeq 4 seq1   -- Output: False
```

---

### 🧠 Explanation

- **Type Signature**:  
  `elemSeq :: Eq a => a -> Sequence a -> Bool`  
  - Requires `Eq a` so we can compare values using `==`.

- **Base Case**:  
  If the sequence is `End`, return `False`.

- **Recursive Case**:  
  Compare the current node’s value with the target:
  - If equal, return `True`
  - Otherwise, continue checking the next node

- Works generically for any type `a` that supports equality (e.g. `Int`, `String`, tuples, etc.)

---

