HC5T10: Combining Higher-Order Functions

---



```haskell
-- Function that checks if any squared value in a list is greater than 50
anySquareGreaterThan50 :: [Int] -> Bool
anySquareGreaterThan50 = any (> 50) . map (^2)
```

---

### 🧠 Explanation

- Type:  
  anySquareGreaterThan50 :: [Int] -> Bool  
  It takes a list of integers and returns True if any of their squares are greater than 50.

- Breakdown:
  - map (^2): Squares each element in the list.
  - any (> 50): Checks if any of the squared values are greater than 50.
  - Function composition (.) is used to combine them into a single point-free expression.

- Note: filter is not strictly necessary here, since any can directly check the condition after mapping. But if you want to include filter explicitly, here's an alternative version:

---

### 🔁 Alternative with filter (less efficient but uses all three)

```haskell
-- Alternative version using filter, map, and any
anySquareGreaterThan50' :: [Int] -> Bool
anySquareGreaterThan50' = any (> 50) . filter (> 0) . map (^2)
```



---



```haskell
*Main> anySquareGreaterThan50 [3, 5, 8]
True  -- 8^2 = 64 > 50

*Main> anySquareGreaterThan50 [1, 2, 3, 4, 5, 6]
False  -- max square is 36

*Main> anySquareGreaterThan50 []
False
```

