 HC16T5: Define a function to convert all characters in a string to uppercase.


---


```haskell
import Data.Char (toUpper)

-- Function to convert all characters to uppercase
toUpperString :: String -> String
toUpperString str = map toUpper str

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🔤 Enter a string to convert to uppercase:"
    input <- getLine
    let result = toUpperString input
    putStrLn $ "🔠 Uppercase result: " ++ result
```

---

### 🧠 Explanation

- **`import Data.Char (toUpper)`**  
  Brings in the `toUpper` function which converts a single character to uppercase.

- **`map toUpper str`**  
  Applies `toUpper` to every character in the input string using the higher-order function `map`.

- **`main`**  
  - Prompts the user for input.
  - Applies `toUpperString` to the result of `getLine`.
  - Prints the transformed string.

---

