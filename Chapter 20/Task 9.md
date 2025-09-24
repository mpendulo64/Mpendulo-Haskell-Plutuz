HC20T9: replicateMonad with Identity Monad
Implement a function replicateMonad that replicates a value using the Identity monad.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.Identity

-- | replicateMonad replicates a value n times inside the Identity monad
replicateMonad :: Int -> a -> Identity [a]
replicateMonad n x = return (replicate n x)

main :: IO ()
main = do
    let val1 = runIdentity $ replicateMonad 5 "Hello"
    print val1  -- ["Hello","Hello","Hello","Hello","Hello"]

    let val2 = runIdentity $ replicateMonad 3 42
    print val2  -- [42,42,42]
```

---

### ✅ **Explanation**

1. **Identity Monad**

   ```haskell
   newtype Identity a = Identity { runIdentity :: a }
   ```

   * `Identity` is a trivial monad that just wraps a value.
   * `return` simply wraps a value in `Identity`.
   * `>>=` applies a function to the contained value.

2. **replicateMonad**

   ```haskell
   replicateMonad :: Int -> a -> Identity [a]
   replicateMonad n x = return (replicate n x)
   ```

   * Uses `replicate :: Int -> a -> [a]` to create a list of length `n` filled with `x`.
   * Wraps the resulting list in the Identity monad with `return`.

3. **Using runIdentity**

   * `runIdentity` extracts the value from the `Identity` monad.
   * Example: `runIdentity $ replicateMonad 5 "Hello"` produces `["Hello","Hello","Hello","Hello","Hello"]`.

---

### ✅ **Why Use Identity Monad**

* It demonstrates monadic operations without side effects.
* Useful when writing generic code that works with any monad (e.g., testing with `Identity` before using `Maybe` or `IO`).

---

