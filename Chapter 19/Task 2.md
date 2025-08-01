HC19T2: Implement a function addThreeApplicative that adds three Maybe Int values using applicative style.
---



```haskell
-- Function to add three Maybe Int values using Applicative style
addThreeApplicative :: Maybe Int -> Maybe Int -> Maybe Int -> Maybe Int
addThreeApplicative x y z = pure (\a b c -> a + b + c) <*> x <*> y <*> z

-- Example usage
main :: IO ()
main = do
    let a = Just 5
    let b = Just 10
    let c = Just 20
    let d = Nothing

    putStrLn "➕ Adding three Maybe Int values:"
    print $ addThreeApplicative a b c   -- Just 35
    print $ addThreeApplicative a b d   -- Nothing
```

---

### 🧠 Explanation

- **`pure (\a b c -> a + b + c)`**:
  - Lifts a 3-argument function into the `Maybe` context.
- **`<*> x <*> y <*> z`**:
  - Applies the function to each `Maybe Int` value.
  - If all are `Just`, it computes the sum.
  - If any are `Nothing`, the result is `Nothing`.

This is the power of the `Applicative` typeclass: it lets you apply functions inside a context (like `Maybe`) without manually unpacking values.

---

