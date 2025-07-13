HC12T9
Write a program that reads a file and prints its content to the terminal. Handle errors gracefully in case the file doesn't exist.
---



```haskell
import System.IO
import System.IO.Error (catchIOError)

-- Function to read and print the file contents safely
readFileSafely :: FilePath -> IO ()
readFileSafely path = do
    catchIOError (do
        content <- readFile path
        putStrLn "📄 File Contents:"
        putStrLn content)
        (\e -> putStrLn $ "❌ Error: " ++ show e)

-- Main function to prompt user and execute
main :: IO ()
main = do
    putStrLn "📥 Enter the file path:"
    filePath <- getLine
    readFileSafely filePath
```

---

### 🧠 Explanation

- **`System.IO` and `System.IO.Error`**:
  - Standard libraries for file I/O and error handling.

- **`readFile :: FilePath -> IO String`**:
  - Reads the entire contents of a file lazily as a string.

- **`catchIOError`**:
  - A handler that catches file-related IO errors.
  - If `readFile` fails (e.g., file doesn’t exist), it prints a readable error message.

- **`main`**:
  - Asks the user to enter a file path.
  - Calls `readFileSafely` to attempt reading and printing the contents.

---



