HC13T10
Create a main function that imports and calls functions from at least two modules (System.Directory, Data.List) to perform a search and display sorted file results.

---


```haskell
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (isInfixOf, sort)

-- Filter and sort files containing the keyword
searchAndSortFiles :: String -> IO [FilePath]
searchAndSortFiles keyword = do
    currentDir <- getCurrentDirectory
    files <- listDirectory currentDir
    let matches = filter (isInfixOf keyword) files
    let sortedMatches = sort matches
    return sortedMatches

-- Main function
main :: IO ()
main = do
    putStrLn "🔍 Enter a search keyword:"
    keyword <- getLine
    results <- searchAndSortFiles keyword
    putStrLn $ "\n📁 Sorted files containing \"" ++ keyword ++ "\":"
    mapM_ putStrLn results
```

---

### 🧠 Explanation

- **`getCurrentDirectory`**: Retrieves your working directory.
- **`listDirectory`**: Lists files and folders in that directory.
- **`isInfixOf keyword`**: Checks whether the keyword exists within each filename.
- **`sort`**: Alphabetically arranges matched filenames.
- **`mapM_ putStrLn results`**: Prints each file on a new line.

---
