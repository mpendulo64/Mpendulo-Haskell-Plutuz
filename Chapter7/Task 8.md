HC7T8: Use Read to parse a value from a string

---



```haskell
import Text.Read (readMaybe)

-- Define the Shape data type
data Shape = Circle Double | Rectangle Double Double deriving (Show, Eq)

-- Define the parseShape function
parseShape :: String -> Maybe Shape
parseShape input =
    case words input of
        ["Circle", rStr] ->
            case readMaybe rStr :: Maybe Double of
                Just r  -> Just (Circle r)
                Nothing -> Nothing
        ["Rectangle", wStr, hStr] ->
            case (readMaybe wStr, readMaybe hStr) of
                (Just w, Just h) -> Just (Rectangle w h)
                _                -> Nothing
        _ -> Nothing

-- Main function to test parseShape
main :: IO ()
main = do
    print (parseShape "Circle 3.5")        -- Just (Circle 3.5)
    print (parseShape "Rectangle 4.0 5.0") -- Just (Rectangle 4.0 5.0)
    print (parseShape "Circle abc")       -- Nothing
    print (parseShape "Triangle 3 4 5")    -- Nothing
```

---

### 📘 **Explanation**

#### ✅ `Shape` Data Type

```haskell
data Shape = Circle Double | Rectangle Double Double
```

* Represents two kinds of shapes: `Circle` (radius) and `Rectangle` (width and height)

---

