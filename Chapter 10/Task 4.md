HC10T4: Create a parameterized type Box a and make it an instance of Eq.

---



```haskell
-- Define the Box data type with one value
data Box a = Empty | Has a
    deriving Show

-- Make Box an instance of Eq
instance Eq a => Eq (Box a) where
    Empty   == Empty   = True
    Has x   == Has y   = x == y
    _       == _       = False

-- Example usage
main :: IO ()
main = do
    let box1 = Has 10
    let box2 = Has 10
    let box3 = Has 20
    let box4 = Empty

    print $ box1 == box2  -- True
    print $ box1 == box3  -- False
    print $ box1 == box4  -- False
    print $ box4 == Empty -- True
```

---

### 🧠 Explanation

- **`data Box a = Empty | Has a`**  
  This defines a generic container that either holds a value (`Has a`) or is empty.

- **`instance Eq a => Eq (Box a)`**  
  The `Eq` constraint ensures we can compare the contents (`a`) inside the box.

- **Equality Logic**:
  - Two `Empty` boxes are equal.
  - Two `Has` boxes are equal if their contents are equal.
  - Any mismatch (e.g., `Empty` vs. `Has`) returns `False`.

---

