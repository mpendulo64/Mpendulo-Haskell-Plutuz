HC19T8: Implement a custom function discardSecond that uses the <* operator to return the first argument after sequencing effects.
---


```haskell
-- Custom function using <* to discard the second result
discardSecond :: IO a -> IO b -> IO a
discardSecond = (<*)

-- Example usage
main :: IO ()
main = do
    result <- discardSecond (putStrLn "✅ First effect runs and result is kept") 
                            (putStrLn "❌ Second effect runs but result is discarded")
    putStrLn "🎯 Done sequencing effects."
```

---

### 🧠 Explanation

- **`(<*) :: Applicative f => f a -> f b -> f a`**:
  - Runs both effects.
  - Keeps the result of the first (`f a`), discards the second (`f b`).

- **`discardSecond`**:
  - A wrapper around `<*` for clarity and reuse.
  - Makes intent explicit: “run both, keep the first.”

- **`main`**:
  - Demonstrates sequencing two `IO` actions.
  - The second message is printed, but its result is ignored.

---

