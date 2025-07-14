HC13T1
Create a program that lists all files in the current directory using the System.Directory module.
---



```haskell
import System.Directory (getCurrentDirectory, listDirectory)

-- Main program to list files in the current directory
main :: IO ()
main = do
    currentDir <- getCurrentDirectory
    putStrLn $ "📂 Current Directory: " ++ currentDir

    files <- listDirectory currentDir
    putStrLn "📁 Contents:"
    mapM_ putStrLn files
```

---

### 🧠 Explanation

- **`getCurrentDirectory`**  
  Fetches the path of the current working directory as a `String`.

- **`listDirectory`**  
  Returns a list of file and folder names (not full paths) in the specified directory — here, it's the current one.

- **`mapM_ putStrLn files`**  
  Iterates through the list and prints each filename individually.

- This program runs in any environment where Haskell can access the filesystem — like GHC or GHCi on your local machine.

---

