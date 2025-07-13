HC12T8
Define a function mergeLists that merges two sorted lists into a single sorted list. Use the main function to test this functionality
---


```haskell
-- Function to merge two sorted lists
mergeLists :: Ord a => [a] -> [a] -> [a]
mergeLists xs [] = xs
mergeLists [] ys = ys
mergeLists (x:xs) (y:ys)
    | x <= y    = x : mergeLists xs (y:ys)
    | otherwise = y : mergeLists (x:xs) ys

-- Main function to test it
main :: IO ()
main = do
    let list1 = [1, 3, 5, 7]
    let list2 = [2, 4, 6, 8, 10]
    let merged = mergeLists list1 list2
    putStrLn "📦 Merged sorted list:"
    print merged
```

---

### 🧠 Explanation

- **Function Signature**:  
  `mergeLists :: Ord a => [a] -> [a] -> [a]`  
  - Takes two lists of any ordered type `a`.  
  - Returns a new sorted list.

- **Base Cases**:  
  - If either list is empty, return the other.

- **Recursive Case**:  
  - Compare the head elements of both lists.
  - Pick the smaller one and recurse on the rest.

- **Efficient Pattern Matching**:  
  - Makes use of Haskell’s lazy evaluation so it doesn’t evaluate more than necessary.

---
