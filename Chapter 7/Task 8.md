HC17T8: Write a function foldWithSemigroup that accepts any list of a type with a Semigroup instance and combines all elements using foldr.
---


```haskell
-- This function requires a Semigroup instance and handles non-empty lists
foldWithSemigroup :: Semigroup a => [a] -> Maybe a
foldWithSemigroup []     = Nothing
foldWithSemigroup (x:xs) = Just (foldr (<>) x xs)

-- Sample usage with lists, which are Semigroups under concatenation
main :: IO ()
main = do
    let strings = ["Hello", " ", "World", "!"]
    let result = foldWithSemigroup strings
    case result of
        Just r  -> putStrLn $ "🧵 Combined string: " ++ r
        Nothing -> putStrLn "⚠️ Empty list, no result"
```

---

### 🧠 Explanation

- **Semigroup typeclass** defines the operator `(<>)` for combining values.
- We use **`foldr (<>) x xs`**, which starts folding from the right with the first element as the initial accumulator.
- **Why `Maybe`?** Because `Semigroup` doesn’t require an identity (`mempty`), so folding an empty list would be undefined.
- **Case handling**:
  - `Nothing` for an empty input.
  - `Just result` for a successful combination.

---

