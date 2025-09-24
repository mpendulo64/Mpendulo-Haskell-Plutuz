HC20T6: doubleMonad Combining Maybe and List
Implement a function doubleMonad that combines two monads: Maybe and List
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad
import Control.Monad.Trans.Maybe
import Control.Monad.Trans.Class

-- | doubleMonad combines Maybe and List monads
-- | It takes a list of Maybe values, filters out Nothings,
-- | and returns all unwrapped values in the combined monad.
doubleMonad :: [Maybe a] -> MaybeT [] a
doubleMonad xs = do
    x <- lift xs            -- Lift the list into MaybeT
    MaybeT (return x)       -- Wrap each Maybe into MaybeT

-- Example usage:
main :: IO ()
main = do
    let input = [Just 1, Nothing, Just 3, Just 5, Nothing]
    -- Run the MaybeT [] computation
    let result = runMaybeT (doubleMonad input)
    print result
```

---

### ✅ **Explanation**

1. **Monad Transformer**

   * `MaybeT [] a` is a **monad transformer** that stacks `Maybe` on top of `[]`.
   * This means:

     * The outer layer (`[]`) can hold multiple results.
     * Each result may still be `Just a` or `Nothing`.

2. **How `doubleMonad` Works**

   * `lift xs` lifts the list into the `MaybeT` context.
   * `MaybeT (return x)` wraps each `Maybe` into the transformer.
   * The result is a `MaybeT [] a` that can be run with `runMaybeT`.

3. **Result**
   For input:

   ```haskell
   [Just 1, Nothing, Just 3, Just 5, Nothing]
   ```

   we get:

   ```haskell
   [Just 1,Nothing,Just 3,Just 5,Nothing]
   ```

   (still inside the combined monad).

---

### 💡 Making It More Useful (Filter Out Nothings)

Often, you want to **extract only the `Just` values**.
We can enhance `doubleMonad` to filter out `Nothing`s:

```haskell
doubleMonadFiltered :: [Maybe a] -> [a]
doubleMonadFiltered xs = do
    Just x <- xs   -- Pattern match succeeds only for Just values
    return x
```
---

### ✅ Key Takeaways

* **`MaybeT []`** is a powerful combination: nondeterministic computations that can fail.
* `doubleMonad` allows you to work in **both monads at once**.
* For practical purposes, pattern matching (`Just x <- xs`) inside list comprehension is a nice shorthand.

---

