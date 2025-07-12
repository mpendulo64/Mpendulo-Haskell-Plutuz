HC9T5: Create a Parametric Data Type with Record Syntax

---



```haskell
-- Define a parametric data type Shape with a color field
data Shape a
    = Circle Float a         -- radius and color
    | Rectangle Float Float a -- width, height, and color
    deriving Show

-- Example usage
main :: IO ()
main = do
    let redCircle = Circle 5.0 "Red"
    let blueRectangle = Rectangle 10.0 5.0 "Blue"
    
    print redCircle       -- Output: Circle 5.0 "Red"
    print blueRectangle   -- Output: Rectangle 10.0 5.0 "Blue"
```

---

### 🧠 Explanation

- **`data Shape a`**:  
  This is a parametric (generic) type where `a` represents the type of the color field. This allows great flexibility—you could use `String`, a custom `Color` type, or even RGB tuples.

- **`Circle Float a`**:  
  Represents a circle with a `Float` radius and a color of type `a`.

- **`Rectangle Float Float a`**:  
  Represents a rectangle with a `Float` width and height, plus a color of type `a`.

- **`deriving Show`**:  
  Automatically gives a printable representation.

---

