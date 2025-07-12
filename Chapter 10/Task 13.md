HC11T3: Define a Container type class with the methods isEmpty, contains, and replace, then implement an instance for the Box type.

---



```haskell
-- Define the Box data type
data Box a = Empty | Has a
    deriving (Show, Eq)

-- Define the Container type class
class Container c where
    isEmpty  :: c a -> Bool
    contains :: Eq a => c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Make Box an instance of Container
instance Container Box where
    isEmpty Empty     = True
    isEmpty (Has _)   = False

    contains Empty _  = False
    contains (Has x) y = x == y

    replace _ newVal  = Has newVal

-- Example usage
main :: IO ()
main = do
    let box1 = Empty :: Box Int
    let box2 = Has 42

    print $ isEmpty box1           -- True
    print $ isEmpty box2           -- False
    print $ contains box2 42       -- True
    print $ contains box2 99       -- False
    print $ replace box1 7         -- Has 7
    print $ replace box2 99        -- Has 99
```

---

### 🧠 Explanation

- **`Container` Type Class**:
  - `isEmpty`: Checks if the container has no content.
  - `contains`: Checks if a given value is inside the container (`Eq a` constraint ensures we can compare values).
  - `replace`: Replaces whatever is inside with a new value.

- **Instance for `Box`**:
  - `isEmpty` pattern matches on `Empty` vs. `Has _`.
  - `contains` compares the boxed value using equality.
  - `replace` always returns a new `Has` box regardless of its original state.

- **Generic Design**:
  - `Container` is parametrically polymorphic — works with any type constructor `c` (like `Box`, `Maybe`, etc.).

---

