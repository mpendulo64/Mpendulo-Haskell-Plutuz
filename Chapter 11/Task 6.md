-- HC11T6: Write a program that reads a line of input, converts it to uppercase, and prints it.


---



```haskell
import Data.Char (toUpper)

-- Program to convert input to uppercase
main :: IO ()
main = do
    putStrLn "🔤 Enter a line to convert to UPPERCASE:"
    input <- getLine
    let uppercase = map toUpper input
    putStrLn $ "🔊 Uppercase version: " ++ uppercase
```

---

### 🧠 Explanation

- **`import Data.Char (toUpper)`**:  
  Brings in the `toUpper` function to transform individual characters.

- **`getLine`**:  
  Reads a full line of text from user input.

- **`map toUpper input`**:  
  Applies `toUpper` to each character in the input string using `map`.

- **`putStrLn $ "..." ++ uppercase`**:  
  Prints the transformed string as part of a response.

---

