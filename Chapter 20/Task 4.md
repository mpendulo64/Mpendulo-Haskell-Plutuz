HC20T4: countChars with State Monad
Implement a function countChars that counts occurrences of a character in a string using the State monad.

Here’s the **working code**:

```haskell
module Main where

import Control.Monad.State

-- | countChars counts occurrences of a given character in a string
-- | using the State monad to keep track of the running count.
countChars :: Char -> String -> Int
countChars ch str = execState (mapM_ step str) 0
  where
    step :: Char -> State Int ()
    step c = do
        count <- get                 -- Get current state (count)
        when (c == ch) (put (count + 1)) -- Increment if match

main :: IO ()
main = do
    let text = "haskell is awesome"
    putStrLn $ "Text: " ++ text
    putStrLn $ "Count of 's': " ++ show (countChars 's' text)
    putStrLn $ "Count of 'a': " ++ show (countChars 'a' text)
    putStrLn $ "Count of 'z': " ++ show (countChars 'z' text)
```

---

### ✅ **Explanation**

1. **Type Signature**

   ```haskell
   countChars :: Char -> String -> Int
   ```

   * Takes a character and a string.
   * Returns an `Int` representing the number of times the character appears.

2. **State Monad**

   * `State Int` holds the running count as we process the string.
   * We start with `0` using `execState ... 0`.

3. **Processing Each Character**

   * `mapM_ step str` iterates through the string, calling `step` for each character.
   * `step` uses:

     * `get` to fetch the current count.
     * `when (c == ch)` to check if current character matches.
     * `put (count + 1)` to update the count when there's a match.

4. **Returning the Result**

   * `execState` runs the stateful computation and returns the **final state** (our count).

---

