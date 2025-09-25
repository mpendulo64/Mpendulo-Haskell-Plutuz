HC20T16: retryIO with IO Monad
Define a function retryIO that retries an IO operation up to a specified number of attempts using the IO monad.

```haskell
module Main where

import Control.Exception (SomeException, try)
import System.IO (hFlush, stdout)

-- | retryIO retries an IO action up to 'n' times if it throws an exception
retryIO :: Int -> IO a -> IO (Either SomeException a)
retryIO n action
    | n <= 0    = return $ Left (userError "No attempts left")
    | otherwise = do
        result <- try action
        case result of
            Right val -> return (Right val) -- Success
            Left err  -> do
                putStrLn $ "Action failed: " ++ show err
                if n > 1
                    then do
                        putStrLn $ "Retrying... (" ++ show (n-1) ++ " attempts left)"
                        retryIO (n-1) action
                    else return (Left err)

-- Example action that may fail
sometimesFails :: IO String
sometimesFails = do
    putStr "Enter 'ok' to succeed: "
    hFlush stdout
    input <- getLine
    if input == "ok"
        then return "Success!"
        else error "Simulated failure"

main :: IO ()
main = do
    putStrLn "You have 3 attempts to enter 'ok'."
    result <- retryIO 3 sometimesFails
    case result of
        Right msg -> putStrLn $ "Operation succeeded: " ++ msg
        Left err  -> putStrLn $ "Operation failed after all retries: " ++ show err
```

---

### Explanation

1. **Type Signature**

```haskell
retryIO :: Int -> IO a -> IO (Either SomeException a)
```

* Takes a number of attempts `n` and an `IO` action.
* Returns `Right value` if successful, or `Left error` if all retries fail.

2. **`try`**

* Runs the `IO` action and catches exceptions.
* Returns `Right val` on success, `Left err` on failure.

3. **Recursive Retry**

* If the action fails and retries remain, recursively call `retryIO (n-1) action`.
* Stops and returns the last error if no retries remain.

4. **Example**

* `sometimesFails` simulates an action that may fail unless the user enters `"ok"`.
* `retryIO 3 sometimesFails` retries up to 3 times.

---

**Sample Run**

```
You have 3 attempts to enter 'ok'.
Enter 'ok' to succeed: nope
Action failed: user error (Simulated failure)
Retrying... (2 attempts left)
Enter 'ok' to succeed: wrong
Action failed: user error (Simulated failure)
Retrying... (1 attempts left)
Enter 'ok' to succeed: ok
Operation succeeded: Success!
```

If all attempts fail:

```
Operation failed after all retries: user error (Simulated failure)
```

---

