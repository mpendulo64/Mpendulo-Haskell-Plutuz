HC9T2: Implement a Parametric Data Type
---



```haskell
-- Define the Box type with two constructors
data Box a = Empty | Has a
    deriving Show

-- Example usage
main :: IO ()
main = do
    let emptyBox = Empty :: Box Int
    let fullBox = Has 42
    print emptyBox   -- Output: Empty
    print fullBox    -- Output: Has 42
```

---

### 🧠 Explanation:

- **`data Box a = Empty | Has a`**
  - This defines a polymorphic type `Box` which can hold values of any type `a`.
  - `Empty` represents a box without contents.
  - `Has a` wraps a value of type `a` — like putting something inside the box.

- **`deriving Show`**
  - Enables printing `Box` values directly in the console.



