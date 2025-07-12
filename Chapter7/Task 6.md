HC7T6: Use the Integral and Floating type classes
---



```haskell
-- circleCircumference works with both Integral and Floating inputs
circleCircumference :: (Real a) => a -> Double
circleCircumference r = 2 * pi * realToFrac r

-- Main function to test with different types
main :: IO ()
main = do
    print (circleCircumference (5 :: Int))       -- Output: 31.41592653589793
    print (circleCircumference (7.5 :: Float))   -- Output: 47.12388980384689
    print (circleCircumference (10 :: Integer))  -- Output: 62.83185307179586
```

---

### 📘 **Explanation**

#### ✅ Function Signature

```haskell
circleCircumference :: (Real a) => a -> Double
```

* `Real a =>` means any type `a` that is an instance of `Real`, which includes:

  * All `Integral` types (like `Int`, `Integer`)
  * All `Floating` types (like `Float`, `Double`)
* We return a `Double` to ensure proper precision and support for floating-point operations.

---




