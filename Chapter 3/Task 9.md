HC3T9 - Advanced Task 9: Find the maximum of three numbers using let

```haskell
-- Function to find the maximum of three integers using let bindings
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree x y z =
    let maxXY = max x y       -- Find the maximum between x and y
        maxXYZ = max maxXY z  -- Compare that result with z
    in maxXYZ

-- Testing the function with sample inputs
main :: IO ()
main = do
    putStrLn $ "maxOfThree 10 20 15 = " ++ show (maxOfThree 10 20 15)  -- Should print 20
    putStrLn $ "maxOfThree 5 25 10 = "  ++ show (maxOfThree 5 25 10)   -- Should print 25
```

---

### 🧠 Explanation

- We define the type signature: `maxOfThree :: Int -> Int -> Int -> Int`.
- Inside the function body:
  - `let maxXY = max x y` stores the greater of the first two numbers.
  - `let maxXYZ = max maxXY z` compares that result with the third number.
- The final result is returned using `in maxXYZ`.

