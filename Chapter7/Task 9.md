HC7T9: Define a type class with multiple instances
---



```haskell
-- Define the Shape data type
data Shape = Circle Double | Rectangle Double Double deriving (Show)

-- Define the Describable type class
class Describable a where
    describe :: a -> String

-- Implement Describable for Bool
instance Describable Bool where
    describe True  = "This is True"
    describe False = "This is False"

-- Implement Describable for Shape
instance Describable Shape where
    describe (Circle r)      = "A circle with radius " ++ show r
    describe (Rectangle w h) = "A rectangle with width " ++ show w ++ " and height " ++ show h

-- Main function to test describe
main :: IO ()
main = do
    print $ describe True
    print $ describe False
    print $ describe (Circle 5.0)
    print $ describe (Rectangle 3.0 4.0)
```

---

### 📘 **Explanation**



```haskell
class Describable a where
    describe :: a -> String
```

* Defines a **type class** named `Describable`.
* Requires an implementation of the method `describe` which converts a value of type `a` to a `String` description.

---

