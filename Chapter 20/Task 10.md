HC20T10: Nested StateT and MaybeT Transformer
Implement a nested monad transformer that combines StateT and MaybeT.
We’ll create a small example where:

* `StateT` keeps track of a counter.
* `MaybeT` allows computations to fail.

This demonstrates how to **layer monads** for combined effects.

---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.Trans.State
import Control.Monad.Trans.Maybe
import Control.Monad.Trans.Class (lift)
import Control.Monad (when)

-- | Type alias for our combined monad
type MyMonad a = MaybeT (StateT Int IO) a

-- | Increment the counter and optionally fail if a condition is met
incrementAndCheck :: Int -> MyMonad Int
incrementAndCheck x = do
    -- Get current state (counter)
    count <- lift get
    let newCount = count + x

    -- Update the state
    lift $ put newCount

    -- Fail if newCount exceeds 10
    when (newCount > 10) $ MaybeT $ return Nothing

    -- Return new count
    return newCount

-- | Example program using the nested monad
program :: MyMonad Int
program = do
    incrementAndCheck 3   -- counter: 0 -> 3
    incrementAndCheck 4   -- counter: 3 -> 7
    incrementAndCheck 5   -- counter: 7 -> 12 (fails here)
    incrementAndCheck 1   -- won't run

main :: IO ()
main = do
    -- Run the nested monad transformer
    result <- runStateT (runMaybeT program) 0
    print result  -- Output: (Nothing,12)
```

---

### ✅ **Explanation**

1. **Monad Stack**

   ```haskell
   type MyMonad a = MaybeT (StateT Int IO) a
   ```

   * **`MaybeT`**: allows computations to fail (`Nothing`).
   * **`StateT Int IO`**: maintains a mutable counter (`Int`) and allows IO operations.
   * Layering allows combining **state + failure + IO** in one computation.

2. **Using `lift`**

   * `lift` is used to access operations from the inner monad (`StateT`) while inside `MaybeT`.
   * Example:

     ```haskell
     count <- lift get
     lift $ put newCount
     ```

3. **Failing the Computation**

   ```haskell
   when (newCount > 10) $ MaybeT $ return Nothing
   ```

   * If the counter exceeds 10, we fail the computation using `MaybeT`.

4. **Running the Monad**

   ```haskell
   runStateT (runMaybeT program) 0
   ```

   * `runMaybeT program` produces `StateT Int IO (Maybe Int)`.
   * `runStateT ... 0` runs the state starting at 0.
   * The result is `(Nothing, 12)`, meaning the computation failed after the counter reached 12.

---

* `Nothing`: computation failed due to the guard.
* `12`: final state of the counter.

---

This pattern is extremely useful for **stacking multiple effects** (state, failure, logging, IO) in a clean, composable way.

---

