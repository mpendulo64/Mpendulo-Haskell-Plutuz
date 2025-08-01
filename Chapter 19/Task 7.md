HC19T7: Write a function conditionalPrint using when that prints a message only when a given condition is true.
---



```haskell
import Control.Monad (when)

-- Function that prints a message only when the condition is True
conditionalPrint :: Bool -> String -> IO ()
conditionalPrint condition message = when condition (putStrLn message)

-- Example usage
main :: IO ()
main = do
    conditionalPrint True  "✅ This message is printed."
    conditionalPrint False "❌ This message is skipped."
```

---

### 🧠 Explanation

- **`when :: Applicative f => Bool -> f () -> f ()`**:
  - Executes the effect only if the condition is `True`.
  - If the condition is `False`, it does nothing.

- **`conditionalPrint`**:
  - Takes a `Bool` and a `String`.
  - Uses `when` to conditionally run `putStrLn`.

- **`main`**:
  - Demonstrates both cases: one where the message is printed, and one where it's skipped.

---

