HC20T20: batchProcessing with Monadic Bind
Write a function batchProcessing that chains multiple monadic actions together using >>= (bind).


We’ll use the `IO` monad for demonstration, but the pattern works for any monad.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

-- Example monadic actions
action1 :: IO Int
action1 = do
    putStrLn "Performing action 1..."
    return 10

action2 :: Int -> IO Int
action2 x = do
    putStrLn $ "Performing action 2 with input: " ++ show x
    return (x * 2)

action3 :: Int -> IO String
action3 x = do
    putStrLn $ "Performing action 3 with input: " ++ show x
    return ("Result is " ++ show x)

-- | Chain multiple monadic actions using >>= (bind)
batchProcessing :: IO String
batchProcessing =
    action1 >>= \a ->
    action2 a >>= \b ->
    action3 b

main :: IO ()
main = do
    result <- batchProcessing
    putStrLn $ "Final output: " ++ result
```

---

### ✅ **Explanation**

1. **Bind `(>>=)`**

   * `m >>= f` runs the monadic action `m`, then passes its result to the function `f`.
   * Each subsequent action can depend on the previous result.

2. **Chaining Actions**

   * `action1 >>= \a -> action2 a` runs `action1`, then passes the result `a` to `action2`.
   * `action2 b >>= \b -> action3 b` continues the chain.

3. **Execution Order**

   * Actions are executed **sequentially**, left to right.
   * Each action can have side effects (like `putStrLn`).

---


