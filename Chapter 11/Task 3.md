-- HC11T3: Write a program that asks the user for a number, reads it, and prints that number multiplied by 2.


---



```haskell
-- Program to read a number and print twice its value
main :: IO ()
main = do
    putStrLn "🔢 Please enter a number:"
    input <- getLine
    let number = read input :: Int
    putStrLn $ "🧮 " ++ show number ++ " multiplied by 2 is " ++ show (number * 2)
```

---

### 🧠 Explanation

- **`putStrLn`** prints a prompt to the user.
- **`getLine`** reads a line from standard input.
- **`read input :: Int`** converts the string input to an integer.
- **`number * 2`** computes twice the value.
- **`show`** is used to convert both numbers back to strings for printing.
- The final output line combines the input and result using string concatenation (`++`).

---

