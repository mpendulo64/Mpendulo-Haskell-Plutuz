HC19T4: Create a function liftAndMultiply that lifts a binary function (Int -> Int -> Int) using liftA2.
---



```haskell
import Control.Applicative (liftA2)

-- Function to lift a binary function using liftA2
liftAndMultiply :: Maybe Int -> Maybe Int -> Maybe Int
liftAndMultiply = liftA2 (*)

-- Example usage
main :: IO ()
main = do
    let x = Just 6
    let y = Just 7
    let z = Nothing

    putStrLn "✖️ Multiplying Maybe Int values using liftA2:"
    print $ liftAndMultiply x y   -- Just 42
    print $ liftAndMultiply x z   -- Nothing
```

---

### 🧠 Explanation

- **`liftA2 :: Applicative f => (a -> b -> c) -> f a -> f b -> f c`**:
  - Takes a binary function and lifts it into an applicative context (like `Maybe`).
  - Applies the function if both arguments are present (`Just`), otherwise returns `Nothing`.

- **`liftA2 (*)`**:
  - Lifts the multiplication function into the `Maybe` context.

So:
```haskell
liftAndMultiply (Just 6) (Just 7) == Just (6 * 7) == Just 42
liftAndMultiply (Just 6) Nothing  == Nothing
```

---
