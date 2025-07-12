-- HC11T9: Write a program that reads two numbers and prints their sum.


---



```haskell
-- Program to read two numbers and print their sum
main :: IO ()
main = do
    putStrLn "🔢 Enter the first number:"
    input1 <- getLine

    putStrLn "➕ Enter the second number:"
    input2 <- getLine

    let num1 = read input1 :: Int
        num2 = read input2 :: Int
        total = num1 + num2

    putStrLn $ "🧮 The sum is: " ++ show total
```

---

### 🧠 Explanation

- **`getLine`**: Reads input from the user as a `String`.
- **`read input :: Int`**: Converts each input string into an integer.
- **`num1 + num2`**: Calculates the sum.
- **`show total`**: Converts the result back into a string for printing.
- The `do` block ensures the steps execute sequentially inside the `IO` monad.

---

