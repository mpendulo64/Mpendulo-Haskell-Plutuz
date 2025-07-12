HC7T7: Implement a function using Bounded and Enum
---


```haskell
-- Define the Color data type
data Color = Red | Green | Blue deriving (Show, Eq)

-- Define the nextColor function
nextColor :: Color -> Color
nextColor Red   = Green
nextColor Green = Blue
nextColor Blue  = Red  -- Wrap around

-- Main function to test nextColor
main :: IO ()
main = do
    print (nextColor Red)    -- Output: Green
    print (nextColor Green)  -- Output: Blue
    print (nextColor Blue)   -- Output: Red
```

---

### 📘 **Explanation**

#### ✅ Data Type Definition

```haskell
data Color = Red | Green | Blue deriving (Show, Eq)
```

* This defines a `Color` type with three constructors: `Red`, `Green`, and `Blue`.
* We derive `Show` so we can print values, and `Eq` to allow equality comparisons if needed.

---



