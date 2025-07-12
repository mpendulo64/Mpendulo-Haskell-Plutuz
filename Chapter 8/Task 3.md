HC8T3: Define a type Shape with constructors Circle Float and Rectangle Float Float.

```haskell
-- Define Shape type with Circle and Rectangle constructors
data Shape = Circle Float | Rectangle Float Float
    deriving Show

-- Function to calculate the area of a Shape
area :: Shape -> Float
area (Circle r)         = pi * r * r
area (Rectangle w h)    = w * h

-- Example usage
main :: IO ()
main = do
    let c = Circle 5
    let r = Rectangle 10 5
    putStrLn $ "Area of Circle: " ++ show (area c)       -- Output: 78.53982...
    putStrLn $ "Area of Rectangle: " ++ show (area r)    -- Output: 50.0
```

### 🧠 Explanation:

- **`data Shape = Circle Float | Rectangle Float Float`**  
  Declares a custom type `Shape` that can be either a `Circle` (with a radius) or a `Rectangle` (with width and height).

- **`area :: Shape -> Float`**  
  Pattern matches each constructor to compute the correct area:
  - `Circle r → πr²`
  - `Rectangle w h → w × h`


