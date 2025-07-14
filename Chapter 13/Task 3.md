HC13T3
Implement a function that sorts and returns filtered file names from the current directory using both Data.List.sort and Data.List.filter.


---


```haskell
import System.Directory (getCurrentDirectory, listDirectory)
import Data.List (sort, isInfixOf)

-- Function to filter and sort files by substring
getFilteredSortedFiles :: String -> IO [FilePath]
getFilteredSortedFiles keyword = do
    dir <- getCurrentDirectory
    files <- listDirectory dir
    let filtered = filter (isInfixOf keyword) files
    let sorted = sort filtered
    return sorted

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🔍 Enter substring to match filenames:"
    keyword <- getLine
    sortedMatches <- getFilteredSortedFiles keyword
    putStrLn $ "\n📂 Sorted files containing \"" ++ keyword ++ "\":"
    mapM_ putStrLn sortedMatches
```

---

### 🧠 Explanation

- **`getCurrentDirectory`**: Gets the absolute path of the working directory.
- **`listDirectory`**: Fetches all files and folders in that directory.
- **`filter` + `isInfixOf`**: Keeps only filenames that include the given `keyword`.
- **`sort`**: Sorts the filtered list alphabetically.
- **`mapM_ putStrLn`**: Prints each file name on its own line.

---

