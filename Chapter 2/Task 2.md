HC2T2 - Task 2: Function Type Signatures

* **Function signatures** for `add`, `isEven`, and `concatStrings`
* **Implementations** of those functions
* A `main` function to demonstrate their usage

---
```haskell
-- Function that adds two Int values
add :: Int -> Int -> Int
add x y = x + y

-- Function that checks if an Int is even
isEven :: Int -> Bool
isEven x = x `mod` 2 == 0

-- Function that concatenates two Strings
concatStrings :: String -> String -> String
concatStrings s1 s2 = s1 ++ s2

-- Main function to demonstrate usage
main :: IO ()
main = do
    -- Using add
    let sumResult = add 5 7
    putStrLn ("5 + 7 = " ++ show sumResult)

    -- Using isEven
    let evenCheck = isEven 10
    putStrLn ("Is 10 even? " ++ show evenCheck)

    -- Using concatStrings
    let combined = concatStrings "Hello, " "Haskell!"
    putStrLn ("Concatenated string: " ++ combined)
```

---

### ▶️ Example Output

```
5 + 7 = 12
Is 10 even? True
Concatenated string: Hello, Haskell!
```




