HC20T14: mapMFilter Monadic Map-Filter
Implement a monadic function mapMFilter that maps and filters elements using a monad.

The idea:

* Apply a function `f :: a -> m (Maybe b)` to each element.
* Collect results where `f` returns `Just b`, discard results where it returns `Nothing`.

This is very similar to `mapMaybeM` that you might find in some libraries.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad (forM)

-- | mapMFilter applies a monadic function that may produce a result (Just)
--   or discard it (Nothing), collecting only the Just results.
mapMFilter :: Monad m => (a -> m (Maybe b)) -> [a] -> m [b]
mapMFilter f xs = do
    results <- forM xs f
    return [y | Just y <- results]

-- Example: Keep even numbers and double them, discard odd numbers
keepEvenAndDouble :: Int -> IO (Maybe Int)
keepEvenAndDouble x =
    if even x
        then return (Just (x * 2))
        else return Nothing

main :: IO ()
main = do
    putStrLn "Mapping & filtering [1..10] to keep evens and double them:"
    result <- mapMFilter keepEvenAndDouble [1..10]
    print result
```

---

### ✅ **Explanation**

1. **Type Signature**

   ```haskell
   mapMFilter :: Monad m => (a -> m (Maybe b)) -> [a] -> m [b]
   ```

   * Takes a function that works in a monad (`m`) and may discard elements by returning `Nothing`.
   * Returns a monadic action that produces a list of kept values.

2. **forM xs f**

   * Applies `f` to each element `x :: a`, collecting results `[Maybe b]` inside the monad.

3. **List Comprehension**

   ```haskell
   [y | Just y <- results]
   ```

   * Extracts all `Just` values, discards `Nothing`.

4. **Example**

   * `keepEvenAndDouble` keeps even numbers, doubles them, discards odd numbers.
   * The result is a list `[4,8,12,16,20]` when applied to `[1..10]`.

---

