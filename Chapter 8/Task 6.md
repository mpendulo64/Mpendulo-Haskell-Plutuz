HC8T6: Define a type Shape using record syntax with fields center :: (Float, Float), color :: String, and radius :: Float for circles, and width :: Float, height :: Float, and color :: String for rectangles. Create an instance of Shape for a circle and a rectangle.

```haskell
-- Define a Shape type using record syntax for both Circle and Rectangle
data Shape
    = Circle
        { center :: (Float, Float)
        , radius :: Float
        , color  :: String
        }
    | Rectangle
        { width  :: Float
        , height :: Float
        , color  :: String
        }
    deriving Show

-- Create an instance of a circle
circleExample :: Shape
circleExample = Circle
    { center = (0.0, 0.0)
    , radius = 5.0
    , color  = "Red"
    }

-- Create an instance of a rectangle
rectangleExample :: Shape
rectangleExample = Rectangle
    { width  = 10.0
    , height = 5.0
    , color  = "Blue"
    }

-- Example usage
main :: IO ()
main = do
    putStrLn "Circle:"
    print circleExample
    putStrLn "Rectangle:"
    print rectangleExample
```

---

### 🧠 Explanation:

- **`data Shape = Circle {...} | Rectangle {...}`** defines a type `Shape` with two distinct constructors—each with **its own set of fields** using record syntax.
- Fields like `center` and `radius` are specific to `Circle`, while `width` and `height` are specific to `Rectangle`.
- **Shared field** `color` appears in both constructors, even though they’re declared separately—this allows field access but can’t be shared directly across constructors.
- Using `deriving Show` enables pretty-printing in the console for testing.

---

