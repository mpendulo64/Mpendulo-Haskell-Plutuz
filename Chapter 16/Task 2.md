HC16T2: Define a function that checks if a given string is a palindrome.
---


```haskell
import Data.Char (toLower, isAlphaNum)

-- Function to check if a string is a palindrome
isPalindrome :: String -> Bool
isPalindrome str =
    let cleaned = map toLower $ filter isAlphaNum str
    in cleaned == reverse cleaned

-- Main function to test it
main :: IO ()
main = do
    putStrLn "🔍 Enter a string to check for palindrome:"
    input <- getLine
    if isPalindrome input
        then putStrLn "✅ Yes, it's a palindrome!"
        else putStrLn "❌ No, it's not a palindrome."
```

---

### 🧠 Explanation

- **`Data.Char`**: Used to normalize input by:
  - `toLower`: Makes the string case-insensitive.
  - `isAlphaNum`: Keeps only letters and digits, ignoring spaces and punctuation.

- **`reverse cleaned`**: Reverses the normalized string and compares it to the original.

- **`main` Function**:
  - Prompts the user.
  - Reads input with `getLine`.
  - Applies `isPalindrome` and prints the result.

---

