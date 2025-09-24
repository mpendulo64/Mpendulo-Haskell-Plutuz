HC20T1: safeDivide with Maybe Monad

```haskell
module Main where

-- | safeDivide performs division safely using Maybe
-- | Returns Nothing if denominator is zero, otherwise Just result.
safeDivide :: (Eq a, Fractional a) => a -> a -> Maybe a
safeDivide _ 0 = Nothing          -- Fail case (division by zero)
safeDivide x y = Just (x / y)     -- Success case wrapped in Just

main :: IO ()
main = do
    print (safeDivide 10 2)  -- Just 5.0
    print (safeDivide 7 0)   -- Nothing
    print (safeDivide 9 3)   -- Just 3.0
```

---

✅ **How this works:**

* `safeDivide` uses **pattern matching**:

  * If the denominator is `0`, we return `Nothing`.
  * Otherwise, we perform the division and wrap the result in `Just`.
* This uses the `Maybe` monad to signal **failure** (Nothing) or **success** (Just value).
* The `main` function demonstrates how to use `safeDivide` and prints results.

---

