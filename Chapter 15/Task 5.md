HC15T5: Write a safe division function using the Maybe type to avoid divide-by-zero errors.
---



```haskell
-- Safe division using Maybe
safeDiv :: (Eq a, Fractional a) => a -> a -> Maybe a
safeDiv _ 0 = Nothing
safeDiv x y = Just (x / y)

-- Example usage
main :: IO ()
main = do
    let a = 10
        b = 2
        c = 0

    printResult a b
    printResult a c

-- Helper function to display result
printResult :: (Eq a, Fractional a, Show a) => a -> a -> IO ()
printResult x y =
    case safeDiv x y of
        Just result -> putStrLn $ show x ++ " / " ++ show y ++ " = " ++ show result
        Nothing     -> putStrLn $ "Division by zero: " ++ show x ++ " / " ++ show y ++ " is undefined"
```

---

## 📘 Explanation

### ✅ `safeDiv` function

```haskell
safeDiv :: (Eq a, Fractional a) => a -> a -> Maybe a
```

* Takes two numbers `x` and `y`
* If `y == 0`, returns `Nothing` to indicate an error
* Otherwise returns `Just (x / y)`

Using `Maybe` ensures that we **don't crash the program** and can **handle the error explicitly**.

---


