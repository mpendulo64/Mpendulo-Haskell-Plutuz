HC20T19: Writer Monad-based Logging System
Implement a Writer monad-based logging system that tracks function calls and their arguments.


We'll use `Writer [String]` to accumulate log messages as we perform computations.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.Writer

-- | A simple function that logs its calls
add :: Int -> Int -> Writer [String] Int
add x y = do
    tell ["add called with arguments: " ++ show x ++ ", " ++ show y]
    return (x + y)

multiply :: Int -> Int -> Writer [String] Int
multiply x y = do
    tell ["multiply called with arguments: " ++ show x ++ ", " ++ show y]
    return (x * y)

-- | Example computation using both functions
computation :: Writer [String] Int
computation = do
    a <- add 2 3
    b <- multiply a 4
    c <- add b 5
    return c

main :: IO ()
main = do
    let (result, log) = runWriter computation
    putStrLn "Computation result:"
    print result
    putStrLn "\nFunction call log:"
    mapM_ putStrLn log
```

---

### ✅ **Explanation**

1. **`Writer [String] a`**

   * The `Writer` monad carries a **log of type `[String]`** along with a computation result `a`.
   * `tell :: [String] -> Writer [String] ()` appends messages to the log.

2. **Logging Function Calls**

   * Each function (`add` and `multiply`) logs its name and arguments with `tell`.

3. **Chaining Functions**

   * The monadic `do` notation ensures that the log accumulates as we chain multiple function calls.

4. **`runWriter`**

   * Extracts the computation result and the accumulated log.

---

