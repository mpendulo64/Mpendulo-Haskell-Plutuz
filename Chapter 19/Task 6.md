HC19T6: Define the function repeatEffect that repeatedly executes an effect using forever.

---




```haskell
import Control.Monad (forever)

-- Function that repeats an IO effect forever
repeatEffect :: IO () -> IO ()
repeatEffect = forever

-- Example usage: repeatedly print a message
main :: IO ()
main = repeatEffect $ putStrLn "🔁 This will repeat forever..."
```

---

### 🧠 Explanation

- **`forever :: Monad m => m a -> m b`**:
  - Takes an effectful action and repeats it infinitely.
  - Discards the result of each iteration.

- **`repeatEffect`**:
  - Wraps `forever` to make the intent clear: repeat an effect endlessly.

- **Example**:
  - `putStrLn "..."` is executed over and over.
  - You can stop it manually (e.g. with Ctrl+C).

---

