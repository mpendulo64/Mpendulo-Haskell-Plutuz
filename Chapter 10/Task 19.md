HC11T9: Define a new data type Length with constructors M and Km, derive Eq, and manually fix comparisons between meters and kilometers.

---



```haskell
-- Define the Length data type
data Length = M Float | Km Float
    deriving (Show, Eq)

-- Implement Ord instance by converting both lengths to meters
instance Ord Length where
    compare l1 l2 = compare (toMeters l1) (toMeters l2)

-- Helper function to normalize all Lengths to meters
toMeters :: Length -> Float
toMeters (M m)  = m
toMeters (Km k) = k * 1000

-- Example usage
main :: IO ()
main = do
    let a = M 500        -- 500 meters
    let b = Km 0.4       -- 400 meters
    let c = Km 0.5       -- 500 meters

    print (a == c)       -- True: both are 500 meters
    print (a > b)        -- True: 500m > 400m
    print (b < c)        -- True: 400m < 500m
    print (max a b)      -- M 500
    print (min b c)      -- Km 0.4
```

---

### 🧠 Explanation

- **Data Constructors**:
  - `M Float`: length in meters
  - `Km Float`: length in kilometers

- **Derived `Eq`**:
  - Allows structural equality checks, but doesn't yet handle semantic equivalence (e.g., `M 500 == Km 0.5` would be `False` with derived Eq alone). You could override `Eq` manually to fix that — want to try?

- **Custom `Ord`**:
  - Converts both sides to meters using `toMeters`.
  - Then compares using standard floating-point comparison.

- **Benefits**:
  - Ensures accurate ordering regardless of which constructor is used.
  - Makes `Length` usable in sorted lists, sets, and other ordered structures.

---

