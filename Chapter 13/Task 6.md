HC13T6
Create a function that uses Data.Map to convert a list of filtered file names into a key-value map.


---


```haskell
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf, sort)
import qualified Data.Map as Map

-- Filtered + sorted file names mapped to indices
filteredFileMap :: String -> IO (Map.Map FilePath Int)
filteredFileMap keyword = do
    dir <- getCurrentDirectory
    files <- listDirectory dir
    let filteredSorted = sort $ filter (isInfixOf keyword) files
    let indexedPairs = zip filteredSorted [1..]
    return $ Map.fromList indexedPairs

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🔍 Enter substring to filter files:"
    keyword <- getLine
    fileMap <- filteredFileMap keyword
    putStrLn "\n🗂️ Filtered File Map:"
    mapM_ print (Map.toList fileMap)
```

---

### 🧠 Explanation

- **`filter (isInfixOf keyword) files`**: Selects file names containing a substring.
- **`sort`**: Ensures predictable ordering.
- **`zip filteredSorted [1..]`**: Assigns an index to each file (starting from 1).
- **`Map.fromList`**: Converts a list of `(key, value)` pairs into a `Map`.
- **`Map.toList`**: Turns the `Map` back into a list for easy printing.

---

