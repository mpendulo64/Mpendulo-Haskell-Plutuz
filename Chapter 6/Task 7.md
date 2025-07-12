-- HC6T7: Implement a function that takes a list and returns the length of the list.

```haskell
-- Compute the length of a list using recursion
listLength :: [a] -> Int
listLength []     = 0
listLength (_:xs) = 1 + listLength xs
```

### 🧠 Explanation:

- **Base Case**:
  - `listLength [] = 0`  
    When the list is empty, its length is `0`.

- **Recursive Case**:
  - `listLength (_:xs) = 1 + listLength xs`  
    This pattern matches the head (`_`) and the tail (`xs`), discards the head, and adds 1 for each recursive call down the tail.

### 💡 How It Works:

Let’s trace `listLength [10, 20, 30]`:

```haskell
listLength [10, 20, 30]
= 1 + listLength [20, 30]
= 1 + (1 + listLength [30])
= 1 + (1 + (1 + listLength []))
= 1 + (1 + (1 + 0))
= 3
```


