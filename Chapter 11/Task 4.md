-- HC11T4: Write a program that reads two lines of input and prints them concatenated.


---



```haskell
-- Program to read two lines and concatenate them
main :: IO ()
main = do
    putStrLn "📥 Enter the first line:"
    line1 <- getLine

    putStrLn "📥 Enter the second line:"
    line2 <- getLine

    putStrLn $ "🧵 Combined result: " ++ (line1 ++ line2)
```

---

### 🧠 Explanation

- **`putStrLn`**: Prompts the user to input each line.
- **`getLine`**: Reads each line of text as a `String`.
- **`++` operator**: Concatenates the two strings.
- **`show` is not needed**: Since `line1` and `line2` are already `String`, you can use them directly in the final output.

---

