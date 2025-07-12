HC10T9: Implement a type class MinMax with methods minValue :: a and maxValue :: a, and provide instances for Int.

---



```haskell
-- Define the MinMax type class
class MinMax a where
    minValue :: a
    maxValue :: a

-- Implement MinMax for Int
instance MinMax Int where
    minValue = minBound
    maxValue = maxBound
```

---

### 🧠 Explanation

- **`class MinMax a where ...`**  
  Declares a type class with two methods:
  - `minValue :: a` returns the lowest possible value.
  - `maxValue :: a` returns the highest possible value.

- **Instance for `Int`**  
  - The `Int` type in Haskell is already part of the `Bounded` type class.
  - So we reuse `minBound` and `maxBound` from `Bounded` — they're safe and efficient defaults for `Int`.

---



