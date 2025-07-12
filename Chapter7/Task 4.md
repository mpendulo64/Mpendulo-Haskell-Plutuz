HC7T4: Create a custom type and implement Show and Read

* `Circle Double`
* `Rectangle Double Double`


---


```haskell
-- Define the Shape data type
data Shape = Circle Double | Rectangle Double Double

-- Implement the Show instance to allow printing
instance Show Shape where
    show (Circle r) = "Circle " ++ show r
    show (Rectangle w h) = "Rectangle " ++ show w ++ " " ++ show h

-- Implement the Read instance to allow parsing from string
instance Read Shape where
    readsPrec _ input =
        case words input of
            ("Circle" : rStr : _) ->
                case reads rStr of
                    [(r, rest)] -> [(Circle r, unwords rest)]
                    _           -> []
            ("Rectangle" : wStr : hStr : _) ->
                case (reads wStr, reads hStr) of
                    ([(w, _)], [(h, rest)]) -> [(Rectangle w h, unwords rest)]
                    _                       -> []
            _ -> []

-- Main function to test Show and Read
main :: IO ()
main = do
    let s1 = Circle 5.5
    let s2 = Rectangle 3.0 4.0

    -- Print the shapes
    print s1
    print s2

    -- Read shapes from strings
    let s3 = read "Circle 7.2" :: Shape
    let s4 = read "Rectangle 2.0 8.0" :: Shape

    print s3
    print s4
```

---

### 📘 **Explanation**

#### ✅ Data Type

```haskell
data Shape = Circle Double | Rectangle Double Double
```

This defines a `Shape` with:

* A `Circle` that takes one `Double` (radius)
* A `Rectangle` that takes two `Double`s (width and height)

---








