HC12T6
Develop a program that reads a list of integers from the user and prints the list sorted in ascending order.


---



```haskell
import Data.List (sort)

-- Main program to read, sort, and print integers
main :: IO ()
main = do
    putStrLn "📥 Enter a list of integers separated by spaces:"
    input <- getLine
    let numbers = map read $ words input :: [Int]
    let sorted = sort numbers
    putStrLn $ "📊 Sorted list: " ++ show sorted
```

---

### 🧠 Explanation

- **`getLine`**: Reads a single line of input from the user (e.g., `"5 2 9 1"`).
- **`words input`**: Splits the string into a list of substrings based on whitespace: `["5", "2", "9", "1"]`.
- **`map read`**: Converts each string to an `Int`, producing `[5, 2, 9, 1]`.
- **`sort numbers`**: Uses the built-in `sort` function from `Data.List` to return `[1, 2, 5, 9]`.
- **`show sorted`**: Converts the final list back to a string for printing.

---

