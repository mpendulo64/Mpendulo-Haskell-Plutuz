HC16T1: Define a function to reverse a string.
---



```haskell
-- Function to reverse a string
reverseString :: String -> String
reverseString str = reverse str

-- Main function to demonstrate its usage
main :: IO ()
main = do
    putStrLn "🔄 Enter a string to reverse:"
    input <- getLine
    let reversed = reverseString input
    putStrLn $ "🪞 Reversed string: " ++ reversed
```

---

### 🧠 Explanation

- **`reverseString :: String -> String`**  
  Declares a function that takes a string and returns its reversed version.

- **`reverse str`**  
  Uses Haskell’s built-in `reverse` function to reverse a list — in this case, a list of characters.

- **In `main`**:
  - The user is prompted for a string.
  - `getLine` reads the input.
  - `reverseString` is called.
  - The result is printed out.

---

