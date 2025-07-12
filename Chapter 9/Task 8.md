HC9T8: Define a Recursive Sequence Data Type

---



```haskell
-- Recursive data type representing a linear sequence
data Sequence a = End | Node a (Sequence a)
    deriving Show

-- Example sequence: 1 → 2 → 3 → End
exampleSequence :: Sequence Int
exampleSequence = Node 1 (Node 2 (Node 3 End))

-- Function to calculate length of a Sequence
sequenceLength :: Sequence a -> Int
sequenceLength End           = 0
sequenceLength (Node _ next) = 1 + sequenceLength next

-- Example usage
main :: IO ()
main = do
    print exampleSequence         -- Output: Node 1 (Node 2 (Node 3 End))
    print $ sequenceLength exampleSequence  -- Output: 3
```

---

### 🧠 Explanation

- **`data Sequence a = End | Node a (Sequence a)`**:
  - `End` marks the termination of the sequence (like `null` or `nil`).
  - `Node a (Sequence a)` represents a node holding a value of type `a` and pointing to the next node.

- **Recursion**:
  - The type is recursive because `Node` holds another `Sequence a` inside it — like chaining nodes together.

- **`sequenceLength` function**:
  - Traverses the structure.
  - Adds `1` for each node, until reaching `End`.

- **Type Parameter `a`**:
  - Makes this structure generic — you can store anything: numbers, strings, tuples, or even other sequences.

---

