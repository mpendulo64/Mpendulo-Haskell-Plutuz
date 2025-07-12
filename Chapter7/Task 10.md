HC7T10: Use a function with multiple type class constraints
---


```haskell
-- Define the Describable type class
class Describable a where
    describe :: a -> String

-- Example instances for Int and Bool
instance Describable Int where
    describe = show

instance Describable Bool where
    describe True = "True"
    describe False = "False"

-- describeAndCompare function: requires Describable and Ord
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
describeAndCompare x y
    | x >= y    = describe x
    | otherwise = describe y

-- Main to test the function
main :: IO ()
main = do
    print $ describeAndCompare (5 :: Int) 3       -- "5"
    print $ describeAndCompare False True         -- "True"
    print $ describeAndCompare True False         -- "True"
```

---

### 📘 **Explanation**



```haskell
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
```

* `a` must implement both `Describable` (to get description) and `Ord` (to compare).

---

