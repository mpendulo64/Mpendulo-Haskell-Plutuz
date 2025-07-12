HC7T2: Implement an Ord instance for a custom data type
```
Red < Green < Blue
```

---

```haskell
-- Define the custom data type
data Color = Red | Green | Blue

-- Implement Eq so colors can be compared for equality
instance Eq Color where
    Red   == Red   = True
    Green == Green = True
    Blue  == Blue  = True
    _     == _     = False

-- Implement Ord so colors have an ordering: Red < Green < Blue
instance Ord Color where
    compare Red Red     = EQ
    compare Red _       = LT
    compare Green Red   = GT
    compare Green Green = EQ
    compare Green Blue  = LT
    compare Blue Blue   = EQ
    compare Blue _      = GT

-- Allow printing Color values
instance Show Color where
    show Red   = "Red"
    show Green = "Green"
    show Blue  = "Blue"

-- Main function to test ordering
main :: IO ()
main = do
    let c1 = Red
    let c2 = Green
    let c3 = Blue

    print (c1 < c2)     -- True
    print (c2 < c3)     -- True
    print (c3 > c1)     -- True
    print (c1 > c1)     -- False
    print (compare c1 c2)  -- LT
    print (compare c2 c2)  -- EQ
```

---

### 📘 **Explanation**

#### ✅ `data Color = Red | Green | Blue`

Defines a **sum type** with three constructors.

---






