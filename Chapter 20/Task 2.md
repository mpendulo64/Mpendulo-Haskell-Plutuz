HC20T2: sequenceMaybe for List of Maybe
Implement a function sequenceMaybe that converts a list of Maybe values into a Maybe of list.


The idea:

* If **any element is `Nothing`**, the whole result is `Nothing`.
* Otherwise, collect all the `Just` values into a list.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

-- | sequenceMaybe converts [Maybe a] into Maybe [a]
sequenceMaybe :: [Maybe a] -> Maybe [a]
sequenceMaybe [] = Just []
sequenceMaybe (x:xs) = case x of
    Nothing -> Nothing
    Just v  -> case sequenceMaybe xs of
                  Nothing -> Nothing
                  Just vs -> Just (v : vs)

-- Example usage
main :: IO ()
main = do
    print $ sequenceMaybe [Just 1, Just 2, Just 3]   -- Just [1,2,3]
    print $ sequenceMaybe [Just 1, Nothing, Just 3]  -- Nothing
    print $ sequenceMaybe []                          -- Just []
```

---

### ✅ **Explanation**

1. **Base Case**

   ```haskell
   sequenceMaybe [] = Just []
   ```

   * An empty list of `Maybe`s becomes `Just []`.

2. **Recursive Case**

   ```haskell
   sequenceMaybe (x:xs) = ...
   ```

   * If `x` is `Nothing`, the whole list fails → return `Nothing`.
   * Otherwise, recursively sequence the rest (`xs`), and prepend the current value `v`.

3. **Behavior**

   * `[Just 1, Just 2, Just 3]` → `Just [1,2,3]`
   * `[Just 1, Nothing, Just 3]` → `Nothing`
   * `[]` → `Just []`

---

This is the manual recursive implementation.

For a **more idiomatic Haskell version**, you can use `foldr`:

```haskell
sequenceMaybe :: [Maybe a] -> Maybe [a]
sequenceMaybe = foldr (\mx acc -> mx >>= \x -> fmap (x:) acc) (Just [])
```

It works the same way but leverages the `>>=` operator for cleaner monadic composition.

---

