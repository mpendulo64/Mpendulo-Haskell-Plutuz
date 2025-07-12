-- HC6T6: Implement a function that determines whether a given element exists in a list.

```haskell
-- Check if an element exists in a list
elementExists :: Eq a => a -> [a] -> Bool
elementExists _ [] = False
elementExists x (y:ys)
    | x == y    = True
    | otherwise = elementExists x ys
```

### 🔍 Explanation:

- **Type Signature**:  
  `Eq a => a -> [a] -> Bool`  
  This means the function works for any type `a` that supports equality (`Eq`), taking a value and a list, and returning a `Bool`.

- **Base Case**:  
  `elementExists _ [] = False`  
  If the list is empty, then the element obviously doesn’t exist.

- **Recursive Case with Guards**:
  - If the head of the list `y` is equal to `x`, return `True`.
  - Otherwise, recurse through the tail `ys`.

