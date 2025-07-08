HC3T10 - Advanced Task 10: Check if a string is a palindrome using recursion and guards

```haskell
-- Function to check if a string is a palindrome using recursion and guards
isPalindrome :: String -> Bool
isPalindrome str
    | length str <= 1              = True
    | head str == last str         = isPalindrome (init (tail str))
    | otherwise                    = False

-- Test cases
main :: IO ()
main = do
    putStrLn $ "\"racecar\" is a palindrome: " ++ show (isPalindrome "racecar")  -- True
    putStrLn $ "\"haskell\" is a palindrome: " ++ show (isPalindrome "haskell")  -- False
    putStrLn $ "\"madam\" is a palindrome: " ++ show (isPalindrome "madam")      -- True
```

---

### 🧠 Explanation:

- **Base case**: If the string has 0 or 1 characters, it's trivially a palindrome → `True`.
- **Recursive case**: If the first and last characters match, recursively check the substring with those characters removed:
  - `tail str` removes the first character.
  - `init ...` removes the last character.
- **Otherwise**, return `False` if the ends don't match.

---

### ✅ Output:

```
"racecar" is a palindrome: True
"haskell" is a palindrome: False
"madam" is a palindrome: True
```

