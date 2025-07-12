HC10T2: Create a type class Summable that provides a sumUp :: [a] -> a. Implement it for the type Int.

---


```haskell
-- Define the Summable type class
class Summable a where
    sumUp :: [a] -> a

-- Implement Summable for Int
instance Summable Int where
    sumUp = sum  -- uses built-in sum for lists of Int

-- Example usage
main :: IO ()
main = do
    let numbers = [1, 2, 3, 4, 5]
    print $ sumUp numbers  -- Output: 15
```

---

### 🧠 Explanation

- **Type Class Definition**:
  - `class Summable a where` defines a new type class for types that can be summed.
  - It requires an implementation of `sumUp :: [a] -> a`.

- **Instance for Int**:
  - We implement `sumUp` using Haskell's built-in `sum` function (which already works on `[Int]`).

- **Usage**:
  - You can now call `sumUp` with a list of `Int` values, and it will return their total.

---

