HC3T5 - Task 5: Determine the type of a triangle using guards

```haskell
-- Function to classify a triangle by its side lengths
triangleType :: Float -> Float -> Float -> String
triangleType a b c
    | a == b && b == c        = "Equilateral"
    | a == b || b == c || a == c = "Isosceles"
    | otherwise               = "Scalene"

-- Testing the function with different triangle types
main :: IO ()
main = do
    putStrLn $ "triangleType 3 3 3: " ++ triangleType 3 3 3   -- "Equilateral"
    putStrLn $ "triangleType 5 5 8: " ++ triangleType 5 5 8   -- "Isosceles"
    putStrLn $ "triangleType 6 7 8: " ++ triangleType 6 7 8   -- "Scalene"
```

---

### 🧠 Explanation:

- `triangleType :: Float -> Float -> Float -> String`: this function takes three floating-point side lengths and returns a string describing the type of triangle.
- We use **guards** to evaluate the conditions:
  - All sides equal → **Equilateral**
  - Any two sides equal → **Isosceles**
  - No sides equal → **Scalene**
- `otherwise` is a catch-all that evaluates to `True` if no prior condition matched.

---


