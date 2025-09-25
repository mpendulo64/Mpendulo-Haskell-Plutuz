HC20T18: MaybeT Monad Transformer for User Input
Create a MaybeT monad transformer to combine Maybe and IO for user input validation.

We’ll use `MaybeT` to:

* Read user input from `IO`.
* Return `Nothing` if validation fails, `Just value` if it succeeds.
* Chain multiple validation steps using monadic composition.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.Trans.Maybe
import Control.Monad.IO.Class (liftIO)
import Data.Char (isDigit, isUpper)

-- | Ask the user for a password, wrapped in MaybeT IO
getPassword :: MaybeT IO String
getPassword = do
    liftIO $ putStrLn "Enter a password:"
    pwd <- liftIO getLine
    if null pwd
        then MaybeT (return Nothing)   -- Fail if empty input
        else return pwd

-- | Validate password using MaybeT
validatePassword :: String -> MaybeT IO String
validatePassword pwd = do
    -- Check minimum length
    if length pwd >= 8
        then return ()
        else MaybeT (return Nothing)

    -- Check for digit
    if any isDigit pwd
        then return ()
        else MaybeT (return Nothing)

    -- Check for uppercase
    if any isUpper pwd
        then return pwd
        else MaybeT (return Nothing)

-- | Combine input + validation using MaybeT
validateUserInput :: MaybeT IO String
validateUserInput = do
    pwd <- getPassword
    validatePassword pwd

main :: IO ()
main = do
    result <- runMaybeT validateUserInput
    case result of
        Just validPwd -> putStrLn $ "✅ Password accepted: " ++ validPwd
        Nothing       -> putStrLn "❌ Invalid password. Please try again."
```

---

### ✅ **Explanation**

1. **`MaybeT` Monad Transformer**

   * Wraps an `IO (Maybe a)` action.
   * Allows chaining computations that may fail (`Nothing`) inside `IO`.

2. **`liftIO`**

   * Used to lift `IO` actions (`putStrLn`, `getLine`) into the `MaybeT` context.

3. **Validation**

   * If any check fails, we return `MaybeT (return Nothing)`.
   * If all pass, we return the password.

4. **`runMaybeT`**

   * Runs the `MaybeT IO` action, giving an `IO (Maybe String)`.
   * We handle success (`Just`) or failure (`Nothing`) in `main`.

---

### ✅ **Example Run**

```
Enter a password:
abcd
❌ Invalid password. Please try again.
```

```
Enter a password:
Abcd1234
✅ Password accepted: Abcd1234
```

---

This pattern is great when you want to short-circuit on failure (like `Maybe`), but still interact with the user (`IO`).

---

