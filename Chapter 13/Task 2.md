HC13T2
Write a function that filters files in the current directory based on a substring in the filename using Data.List.isInfixOf.
---


```haskell
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf)
import Control.Monad (filterM)

-- Function to filter files by substring
filterFilesBySubstring :: String -> IO [FilePath]
filterFilesBySubstring substring = do
    currentDir <- getCurrentDirectory
    files <- listDirectory currentDir
    return $ filter (isInfixOf substring) files

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🔍 Enter the substring to filter filenames:"
    keyword <- getLine
    matches <- filterFilesBySubstring keyword
    putStrLn $ "📂 Files containing \"" ++ keyword ++ "\":"
    mapM_ putStrLn matches
```

---

### 🧠 Explanation

- **`listDirectory currentDir`**:  
  Gets all files and folders (non-recursively) from the current directory.

- **`isInfixOf substring filename`**:  
  Returns `True` if `substring` is found inside `filename`. It's case-sensitive unless you pre-process with something like `map toLower`.

- **`filter (...) files`**:  
  Keeps only the filenames where the condition matches.

- **`main`**:  
  Prompts for a substring, filters the list accordingly, and prints results.

---

 
