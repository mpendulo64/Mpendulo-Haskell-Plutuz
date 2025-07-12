HC7T1: Implement an Eq instance for a custom data type
```haskell
-- Define a custom data type
data Color = Red | Green | Blue

-- Manually implement the Eq type class
instance Eq Color where
    Red   == Red   = True
    Green == Green = True
    Blue  == Blue  = True
    _     == _     = False

-- Show instance to allow printing
instance Show Color where
    show Red   = "Red"
    show Green = "Green"
    show Blue  = "Blue"

-- Main function to demonstrate equality
main :: IO ()
main = do
    let color1 = Red
    let color2 = Green
    let color3 = Red

    putStrLn ("color1 == color2: " ++ show (color1 == color2)) -- False
    putStrLn ("color1 == color3: " ++ show (color1 == color3)) -- True
```

---

### 📘 **Explanation**

#### 🧱 **Custom Data Type**

```haskell
data Color = Red | Green | Blue
```

This defines a new type `Color` with three possible values: `Red`, `Green`, and `Blue`.

---














