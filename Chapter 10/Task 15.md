HC11T5: Create a function guessWhat'sInside that takes a Container and checks if a specific item is inside.

---


```haskell
-- Assume these are already defined:
-- Container type class
class Container c where
    isEmpty  :: c a -> Bool
    contains :: Eq a => c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Sample container type: Box
data Box a = Empty | Has a
    deriving (Show, Eq)

instance Container Box where
    isEmpty Empty     = True
    isEmpty (Has _)   = False

    contains Empty _  = False
    contains (Has x) y = x == y

    replace _ newVal  = Has newVal

-- Function to check whether the item is inside the container
guessWhat'sInside :: (Container c, Eq a) => a -> c a -> String
guessWhat'sInside x c
    | contains c x = "🎯 That was a good guess! It's inside."
    | otherwise    = "❌ Nope, that's not what's inside."

-- Example usage
main :: IO ()
main = do
    let box1 = Has 42
    let box2 = Empty :: Box Int

    putStrLn $ guessWhat'sInside 42 box1  -- 🎯 That was a good guess! It's inside.
    putStrLn $ guessWhat'sInside 99 box1  -- ❌ Nope, that's not what's inside.
    putStrLn $ guessWhat'sInside 10 box2  -- ❌ Nope, that's not what's inside.
```

---

### 🧠 Explanation

- **`guessWhat'sInside`**:
  - Takes a value `x` and a container `c a`.
  - Uses `contains` to check if `x` is inside the container.
  - Returns a user-friendly message depending on the result.

- **Generic Design**:
  - Works for any container type (`Box`, `Present`, etc.) implementing `Container`.
  - Requires `Eq a` so it can compare values.

- **Playful Feedback**:
  - The function is themed to feel like guessing a wrapped gift — perfect for interactive or playful CLI applications.

---

