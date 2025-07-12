HC7T5: Implement a function that uses Num constraints
---



```haskell
-- squareArea function using a polymorphic numeric type
squareArea :: Num a => a -> a
squareArea side = side * side

-- Main function to test squareArea with different numeric types
main :: IO ()
main = do
    print (squareArea (5 :: Int))       -- Output: 25
    print (squareArea (4.5 :: Float))   -- Output: 20.25
    print (squareArea (3.2 :: Double))  -- Output: 10.24
```

---

### 📘 **Explanation**

#### ✅ Function Signature

```haskell
squareArea :: Num a => a -> a
```

* This means `squareArea` takes an argument of type `a` and returns a value of the same type.
* The type `a` must be an instance of the **`Num`** type class, which includes types like `Int`, `Float`, and `Double`.

---




