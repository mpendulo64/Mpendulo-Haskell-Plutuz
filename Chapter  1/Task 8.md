HC1T8 - Task 8: Higher-Order Functions

---

### ✅ **Haskell Code Example**

```haskell
-- Define applyTwice function
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)

-- Example function to use with applyTwice
double :: Int -> Int
double x = x * 2

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "Enter a number:"
    input <- getLine
    let number = read input :: Int
        result = applyTwice double number
    putStrLn ("Result after applying 'double' twice: " ++ show result)
```

---

### ▶️ Example Run

```
Enter a number:
3
Result after applying 'double' twice: 12
```

---

### 📌 Explanation

* `applyTwice f x = f (f x)` — applies the function `f` two times to the input `x`.
* In the example, `double 3 = 6`, then `double 6 = 12`.




