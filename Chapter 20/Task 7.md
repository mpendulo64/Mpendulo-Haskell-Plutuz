HC20T7: findFirst with Either Monad
Create a function findFirst that uses the Either monad to handle errors when finding an element in a list.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Data.List (find)

-- | findFirst takes a predicate and a list, returning
-- | Right the first matching element, or Left an error message.
findFirst :: (a -> Bool) -> [a] -> Either String a
findFirst predicate xs =
    case find predicate xs of
        Just value -> Right value
        Nothing    -> Left "No matching element found."

main :: IO ()
main = do
    let numbers = [10, 20, 30, 40, 50]

    print (findFirst (> 25) numbers)  -- Right 30
    print (findFirst (> 100) numbers) -- Left "No matching element found."
```

---

### ✅ **Explanation**

1. **Type Signature**

   ```haskell
   findFirst :: (a -> Bool) -> [a] -> Either String a
   ```

   * Takes a predicate `(a -> Bool)` and a list `[a]`.
   * Returns an `Either String a`:

     * `Right value` if a matching element is found.
     * `Left "error message"` if no match is found.

2. **How It Works**

   * We use `find` from `Data.List`, which returns a `Maybe a`.
   * We then convert `Maybe` into `Either`:

     * `Just value` → `Right value`
     * `Nothing` → `Left "No matching element found."`

3. **Why Use Either**

   * `Either` allows us to return **a meaningful error message** (unlike `Maybe`, which only gives `Nothing`).
   * It’s also a monad, so we can chain multiple error-prone computations.

---
---

### ✅ **Monadic Chaining Example**

We can easily chain `Either` results using `>>=`:

```haskell
main :: IO ()
main = do
    let numbers = [10, 20, 30, 40, 50]
    let result = do
            x <- findFirst (> 15) numbers
            y <- findFirst (> x) numbers
            return (x, y)

    print result  -- Right (20,30)
```

If any step fails, it stops and returns `Left "No matching element found."`.

---

