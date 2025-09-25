HC20T13: fibonacciMemo with State Monad
Create a function fibonacciMemo using the State monad to memoize Fibonacci calculations.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.State
import qualified Data.Map as M

-- | Fibonacci with memoization using the State monad
fibonacciMemo :: Int -> State (M.Map Int Integer) Integer
fibonacciMemo n
    | n == 0 = return 0
    | n == 1 = return 1
    | otherwise = do
        memo <- get
        case M.lookup n memo of
            Just value -> return value
            Nothing -> do
                a <- fibonacciMemo (n - 1)
                b <- fibonacciMemo (n - 2)
                let value = a + b
                modify (M.insert n value)
                return value

-- | Helper to run fibonacciMemo with an empty memo table
runFibonacciMemo :: Int -> Integer
runFibonacciMemo n = evalState (fibonacciMemo n) M.empty

main :: IO ()
main = do
    putStrLn "Fibonacci numbers (0 to 10) with memoization:"
    mapM_ (\i -> putStrLn $ "fib(" ++ show i ++ ") = " ++ show (runFibonacciMemo i)) [0..10]
```

---

### ✅ **Explanation**

1. **State Monad with `Map`**

   * The state carries a `Map Int Integer` which stores already computed Fibonacci values.
   * `get` retrieves the current map.
   * `modify` updates the map with new results.

2. **Memoization Logic**

   * Check if `n` is already in the memo table (`M.lookup`).
   * If yes, return it immediately (no recomputation).
   * If not, recursively compute `fibonacciMemo (n-1)` and `fibonacciMemo (n-2)`, store the result in the map, and return it.

3. **`evalState`**

   * Runs the stateful computation with an **empty memo table** (`M.empty`).

4. **Efficiency**

   * Without memoization, Fibonacci is `O(2^n)` due to recomputation.
   * With memoization, it becomes `O(n)` since each Fibonacci number is computed once and stored.

---

