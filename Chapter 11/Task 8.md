-- HC11T8: Write a program that reads a number and tells the user if it's even or odd.


---



```haskell
-- Program to check if a number is even or odd
main :: IO ()
main = do
    putStrLn "🔢 Enter a number:"
    input <- getLine
    let number = read input :: Int
    if even number
        then putStrLn $ show number ++ " is even ✅"
        else putStrLn $ show number ++ " is odd 🔷"
```

---

### 🧠 Explanation

- **`putStrLn "..."`**: Prompts the user to enter a number.
- **`getLine`**: Captures input from the console as a `String`.
- **`read input :: Int`**: Converts that string into an integer.
- **`even number`**: Uses Haskell’s built-in `even` function to check if the number is divisible by 2.
- **`if ... then ... else`**: Branches based on the result and prints the outcome.

---

