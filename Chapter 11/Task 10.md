-- HC11T10: Write a program that reads input from the user and reverses the string.


---



```haskell
-- Program to reverse user input
main :: IO ()
main = do
    putStrLn "🔄 Enter a string to reverse:"
    input <- getLine
    let reversed = reverse input
    putStrLn $ "🪞 Reversed: " ++ reversed
```

---

### 🧠 Explanation

- **`getLine`**: Reads a full line of input from the user.
- **`reverse input`**: Haskell's built-in `reverse` function reverses the list of characters (i.e. the string).
- **`putStrLn`**: Prints out the reversed result with a friendly message.

---



