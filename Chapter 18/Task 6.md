HC18T6: Implement a function applyToMaybe that uses fmap to transform the value inside a Maybe.
---




```haskell
-- Function that applies a transformation to a Maybe value using fmap
applyToMaybe :: (a -> b) -> Maybe a -> Maybe b
applyToMaybe = fmap

-- Example usage
main :: IO ()
main = do
    let val1 = Just 10
    let val2 = Nothing

    putStrLn "🔁 Applying (*2) to Maybe values:"
    print $ applyToMaybe (*2) val1   -- Just 20
    print $ applyToMaybe (*2) val2   -- Nothing
```

---

### 🧠 Explanation

- **`Maybe a`**: Represents an optional value — either `Just a` or `Nothing`.
- **`fmap`**:
  - Applies the function to the value inside `Just`.
  - Leaves `Nothing` untouched.
- **`applyToMaybe`**:
  - Generalizes this behavior for any transformation `(a -> b)`.

---


