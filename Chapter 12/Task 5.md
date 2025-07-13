HC12T5
Create a program that defines a function isPalindrome to check whether a given string is a palindrome. Use the main function to test this with user input.
---



```haskell
-- Palindrome checker in Haskell
import Data.Char (toLower, isAlphaNum)

-- Function to normalize and check for palindrome
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
        then putStrLn "✅ It's a palindrome!"
        else putStrLn "❌ Not a palindrome."
```

---

### 🧠 Explanation

- **`isPalindrome :: String -> Bool`**  
  Checks whether the input string, after cleaning, equals its reverse.

- **Normalization**:  
  - `toLower`: makes the comparison case-insensitive.
  - `filter isAlphaNum`: removes spaces and punctuation so only letters and numbers are compared.

- **Comparison**:  
  `cleaned == reverse cleaned` ensures the cleaned string is the same backward and forward.

- **`main` Function**:  
  - Prompts the user for input.
  - Uses `getLine` to read the input string.
  - Prints whether the result is a palindrome or not.

---

