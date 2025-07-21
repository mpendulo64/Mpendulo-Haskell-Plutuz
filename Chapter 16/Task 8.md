 HC16T8: Define a function that sorts a list of integers using the insertion sort algorithm.
---


```haskell
-- Insert one element into a sorted list
insert :: Int -> [Int] -> [Int]
insert x [] = [x]
insert x (y:ys)
    | x <= y    = x : y : ys
    | otherwise = y : insert x ys

-- Recursive insertion sort
insertionSort :: [Int] -> [Int]
insertionSort [] = []
insertionSort (x:xs) = insert x (insertionSort xs)

-- Main function to test it
main :: IO ()
main = do
    let unsorted = [7, 3, 1, 9, 2, 5]
    let sorted = insertionSort unsorted
    putStrLn $ "🔢 Original list: " ++ show unsorted
    putStrLn $ "✅ Sorted list:   " ++ show sorted
```

---

### 🧠 Explanation

- **`insert :: Int -> [Int] -> [Int]`**  
  Inserts an integer into an already-sorted list by comparing it recursively to each element.

- **`insertionSort :: [Int] -> [Int]`**  
  Recursively takes the head of the list and inserts it into the sorted tail.

- **`main`**  
  - Demonstrates usage by sorting a predefined list.
  - Prints both the original and sorted versions.

---

