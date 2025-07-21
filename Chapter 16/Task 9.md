HC16T9: Implement a function to remove duplicates from a list.
---


```haskell
-- Function to remove duplicates from a list
removeDuplicates :: Eq a => [a] -> [a]
removeDuplicates [] = []
removeDuplicates (x:xs)
    | x `elem` xs = removeDuplicates xs
    | otherwise   = x : removeDuplicates xs

-- Main function to demonstrate usage
main :: IO ()
main = do
    let originalList = [1, 2, 3, 2, 4, 1, 5]
    let cleanedList = removeDuplicates originalList
    putStrLn $ "📥 Original list: " ++ show originalList
    putStrLn $ "✅ List without duplicates: " ++ show cleanedList
```

---

### 🧠 Explanation

- **`removeDuplicates :: Eq a => [a] -> [a]`**  
  - Works for any type `a` that supports equality (`Eq`).
  - Processes the list recursively:
    - Base case: empty list returns empty.
    - For each element `x`, checks if it's present later in the list (`xs`).
      - If yes, skip it.
      - If no, keep it and recursively filter the rest.

- This version preserves only the **last occurrence** of each element. Want to preserve the **first** instead? Just flip the check:

```haskell
removeDuplicates (x:xs)
    | x `elem` result = result
    | otherwise       = x : result
  where result = removeDuplicates xs
```

---

