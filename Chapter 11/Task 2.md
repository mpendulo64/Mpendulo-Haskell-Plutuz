-- HC11T2: Write a program that reads a line of input and prints the number of characters in that line.


```haskell
-- Program to count characters in a line
main :: IO ()
main = do
    putStrLn "🔤 Enter a line of text:"
    line <- getLine
    let charCount = length line
    putStrLn $ "📏 Number of characters: " ++ show charCount
```

---

### 🧠 Explanation

- **`main :: IO ()`**  
  Entry point for an interactive Haskell program.

- **`putStrLn`**  
  Prints a prompt to let the user know what to enter.

- **`getLine`**  
  Reads the entire line of text input from the user (including spaces).

- **`length line`**  
  Calculates the number of characters (not words or tokens!) in the line.

- **`show charCount`**  
  Converts the `Int` result to a `String` so it can be concatenated into the final output message.

---

