HC20T17: validatePassword with Either Monad
Implement a function validatePassword that performs multiple checks using the Either monad to return validation errors.
 
 Let's implement **`validatePassword`** using the **Either monad** so we can return descriptive validation errors when a password fails checks.

We'll write multiple checks:

* Minimum length
* Must contain a digit
* Must contain an uppercase letter

If all checks pass, we return `Right password`. Otherwise, we return `Left errorMessage`.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Data.Char (isDigit, isUpper)

-- | Validate password with multiple checks using Either
validatePassword :: String -> Either String String
validatePassword pwd = do
    -- Check minimum length
    if length pwd >= 8
        then return ()
        else Left "Password must be at least 8 characters long."

    -- Check for a digit
    if any isDigit pwd
        then return ()
        else Left "Password must contain at least one digit."

    -- Check for an uppercase letter
    if any isUpper pwd
        then return pwd
        else Left "Password must contain at least one uppercase letter."

-- Example usage
main :: IO ()
main = do
    putStrLn "Enter a password to validate:"
    pwd <- getLine
    case validatePassword pwd of
        Right validPwd -> putStrLn $ "Password is valid: " ++ validPwd
        Left errMsg    -> putStrLn $ "Validation failed: " ++ errMsg
```

---

### ✅ **Explanation**

1. **Type Signature**

   ```haskell
   validatePassword :: String -> Either String String
   ```

   * Returns `Right password` if all checks pass.
   * Returns `Left errorMessage` if any check fails.

2. **Monad Do-Notation**

   * The `Either` monad stops at the first `Left` (error) it encounters.
   * This means as soon as a check fails, we exit and return that error.

3. **Validation Steps**

   * Check **minimum length** (`>= 8`).
   * Check **digit presence** (`any isDigit pwd`).
   * Check **uppercase presence** (`any isUpper pwd`).

4. **Example Interaction**

   * Input: `abc` → `Left "Password must be at least 8 characters long."`
   * Input: `abcdefgh` → `Left "Password must contain at least one digit."`
   * Input: `abcd1234` → `Left "Password must contain at least one uppercase letter."`
   * Input: `Abcd1234` → `Right "Abcd1234"`

---

### ✅ **Sample Run**

```
Enter a password to validate:
Abcd1234
Password is valid: Abcd1234
```

If invalid:

```
Enter a password to validate:
abcd1234
Validation failed: Password must contain at least one uppercase letter.
```

---

