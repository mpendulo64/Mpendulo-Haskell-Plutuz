HC19T5: Implement the function applyEffects using <*>, where it takes a tuple (IO Int, IO Int) and sums the values while printing them.
---



```haskell
-- Function to apply effects and sum two IO Int values using <*>
applyEffects :: (IO Int, IO Int) -> IO Int
applyEffects (ioA, ioB) = pure (+) <*> printAndReturn ioA <*> printAndReturn ioB
  where
    printAndReturn :: IO Int -> IO Int
    printAndReturn action = do
        val <- action
        putStrLn $ "Value: " ++ show val
        return val

-- Example usage
main :: IO ()
main = do
    let a = return 10
    let b = return 25

    putStrLn "🧮 Applying effects and summing IO Int values:"
    result <- applyEffects (a, b)
    putStrLn $ "Sum: " ++ show result
```

---

### 🧠 Explanation

- **`pure (+)`** lifts the `(+)` function into the `IO` context.
- **`<*>`** applies the lifted function to each `IO Int` value.
- **`printAndReturn`** is a helper that:
  - Executes the `IO Int` action.
  - Prints the value.
  - Returns it so it can be used in the sum.

This way, both values are printed before being summed — and all effects are sequenced properly.

---

