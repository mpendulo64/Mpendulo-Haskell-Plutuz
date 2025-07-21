 HC16T7: Write a function that checks if an element exists in a list.
---



```haskell
-- Function to check if an element exists in a list
elementExists :: Eq a => a -> [a] -> Bool
elementExists x xs = elem x xs

-- Main function to demonstrate usage
main :: IO ()
main = do
    let myList = [10, 20, 30, 40, 50]
    let target = 30
    if elementExists target myList
        then putStrLn $ "✅ " ++ show target ++ " exists in the list."
        else putStrLn $ "❌ " ++ show target ++ " does not exist in the list."
```

---

### 🧠 Explanation

- **Type Signature**  
  `elementExists :: Eq a => a -> [a] -> Bool`  
  - Works for any type `a` that supports equality (`Eq`).
  - Takes an element and a list, returns `True` if the element is found.

- **`elem x xs`**  
  - A built-in function that checks if `x` is in the list `xs`.

- **`main` Function**  
  - Defines a sample list and a target value.
  - Calls `elementExists` to check membership and prints the result.

---

