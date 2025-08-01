HC19T9: Implement pureAndApply which demonstrates how pure works with applicative effects.

---



```haskell
-- Demonstrates how pure works with applicative effects
pureAndApply :: IO ()
pureAndApply = do
    let f = pure (\x y -> x + y)  -- Lifted function: IO (Int -> Int -> Int)
    let x = pure 3                -- Lifted value: IO Int
    let y = pure 5                -- Lifted value: IO Int
    result <- f <*> x <*> y       -- Apply function to values inside IO
    putStrLn $ "✅ Result of pureAndApply: " ++ show result
```

---

### 🧠 Explanation

- **`pure :: Applicative f => a -> f a`**:
  - Lifts a plain value into an applicative context.
  - In this case, `pure 3 :: IO Int`.

- **`<*> :: Applicative f => f (a -> b) -> f a -> f b`**:
  - Applies a function inside a context to a value inside the same context.

- **Step-by-step**:
  1. `pure (\x y -> x + y)` lifts a binary function into `IO`.
  2. `pure 3` and `pure 5` lift values into `IO`.
  3. `<*>` applies the function to both values inside the context.
  4. `result` is the final computed value inside `IO`.

---

