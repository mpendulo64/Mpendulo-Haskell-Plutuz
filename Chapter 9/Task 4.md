HC9T4: Extract a Value from a Box

---



```haskell
-- Define the Box type
data Box a = Empty | Has a
    deriving Show

-- Function to extract value from a Box, or return default if empty
extract :: a -> Box a -> a
extract def Empty    = def
extract _   (Has x)  = x

-- Example usage
main :: IO ()
main = do
    let box1 = Empty :: Box Int
    let box2 = Has 99
    print (extract 42 box1)   -- Output: 42
    print (extract 42 box2)   -- Output: 99
```

---

### 🧠 Explanation:

- **Type Signature**:  
  `extract :: a -> Box a -> a`  
  This means it takes:
  - a default value of type `a`
  - a `Box a`
  - and returns a value of type `a`.

- **Pattern Matching**:
  - If the box is `Empty`, return the default value `def`.
  - If the box is `Has x`, return the contained value `x`.

---

