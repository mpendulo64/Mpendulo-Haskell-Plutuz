-- HC6T3: Implement a function to compute the sum of elements in a list using foldr.

```haskell
-- Sum of list elements using foldr
sumList :: [Int] -> Int
sumList xs = foldr (+) 0 xs
```

### 🔍 How It Works:

- **`foldr (+) 0 xs`** means:
  - Start with an **initial value of `0`**
  - Apply the **`+` operator** between each element of the list and the running total
  - The folding starts from the **right** side of the list

