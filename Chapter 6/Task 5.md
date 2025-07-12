-- HC6T5: Implement a function that reverses a list using recursion.

```haskell
-- Reverse a list using recursion
reverseList :: [a] -> [a]
reverseList []     = []
reverseList (x:xs) = reverseList xs ++ [x]
```

### 🔍 Explanation:

- **Base Case**:
  - `reverseList [] = []`  
    If the list is empty, just return an empty list.

- **Recursive Case**:
  - `reverseList (x:xs) = reverseList xs ++ [x]`  
    This says: "Reverse the tail of the list (`xs`), then append the head element (`x`) to the end."

### 🧠 How It Works (Step-by-Step):

Let’s reverse `[1, 2, 3]`:

```haskell
reverseList [1, 2, 3]
=> reverseList [2, 3] ++ [1]
=> (reverseList [3] ++ [2]) ++ [1]
=> ((reverseList [] ++ [3]) ++ [2]) ++ [1]
=> (([] ++ [3]) ++ [2]) ++ [1]
=> ([3] ++ [2]) ++ [1]
=> [3, 2] ++ [1]
=> [3, 2, 1]
```

