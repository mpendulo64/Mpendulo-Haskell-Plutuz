HC20T12: File Reading with IO Monad
Use the IO monad to read a file and display its contents line-by-line.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

main :: IO ()
main = do
    putStrLn "Enter the file name to read:"
    fileName <- getLine               -- Read file name from user
    contents <- readFile fileName     -- Read entire file into a String
    let fileLines = lines contents    -- Split into list of lines
    putStrLn "File contents (line by line):"
    mapM_ putStrLn fileLines          -- Print each line
```

---

### ✅ **Explanation**

1. **`getLine`**
   Reads input from the user — here we ask for the file name.

2. **`readFile`**
   Reads the entire file into a single `String`.
   (Lazy I/O: file contents are read as needed.)

3. **`lines`**
   Splits the `String` into a list of individual lines.

4. **`mapM_ putStrLn`**
   Applies `putStrLn` to each line in the list, printing them one by one.

   * `mapM_` is used for actions with side effects (printing).

---
