HC20T3: Writer Monad Logging Calculator
Create a logging calculator using the Writer monad to keep track of all operations.

```haskell
module Main where

import Control.Monad.Writer

-- | Our Calculator type uses Writer to log steps as Strings
type Calculator a = Writer [String] a

-- | Adds two numbers with logging
add :: Int -> Int -> Calculator Int
add x y = do
    tell ["Adding " ++ show x ++ " and " ++ show y]
    return (x + y)

-- | Subtracts two numbers with logging
subtract' :: Int -> Int -> Calculator Int
subtract' x y = do
    tell ["Subtracting " ++ show y ++ " from " ++ show x]
    return (x - y)

-- | Multiplies two numbers with logging
multiply :: Int -> Int -> Calculator Int
multiply x y = do
    tell ["Multiplying " ++ show x ++ " and " ++ show y]
    return (x * y)

-- | Divides two numbers with logging (safe division)
divide :: Int -> Int -> Calculator (Maybe Int)
divide _ 0 = do
    tell ["Division by zero attempted!"]
    return Nothing
divide x y = do
    tell ["Dividing " ++ show x ++ " by " ++ show y]
    return (Just (x `div` y))

-- | Example program that chains multiple operations
calculatorProgram :: Calculator (Maybe Int)
calculatorProgram = do
    sumResult <- add 10 5
    productResult <- multiply sumResult 2
    divide productResult 3  -- returns Maybe Int

main :: IO ()
main = do
    let (result, logLines) = runWriter calculatorProgram
    putStrLn "---- Calculation Log ----"
    mapM_ putStrLn logLines
    putStrLn "---- Result ----"
    print result
```

---

### ✅ **Explanation**

1. **Writer Monad**

   * `Writer [String] a` represents a computation that produces a value of type `a` **and** a log (`[String]`).
   * We use `tell :: [String] -> Writer [String] ()` to append log messages.

2. **Calculator Functions**

   * Each arithmetic function (`add`, `subtract'`, `multiply`, `divide`) performs the operation and logs what it did.
   * `divide` handles division by zero safely by returning `Nothing`.

3. **Chaining Operations**

   * In `calculatorProgram`, we use **do-notation** to:

     * Add `10` and `5`
     * Multiply result by `2`
     * Divide result by `3`
   * The Writer monad automatically collects all log messages during the process.

4. **Running the Program**

   * `runWriter calculatorProgram` returns a tuple `(result, logs)`
   * We print the log messages first, then the result.

---

