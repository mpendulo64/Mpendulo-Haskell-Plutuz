HC3T4 - Task 4: Calculate the area of a triangle using Heron's formula

```haskell
-- Function to calculate the area of a triangle using Heron's formula
triangleArea :: Float -> Float -> Float -> Float
triangleArea a b c =
    let s = (a + b + c) / 2
    in sqrt (s * (s - a) * (s - b) * (s - c))

-- Testing the function
main :: IO ()
main = do
    putStrLn "Area of triangle with sides 3, 4, 5:"
    print (triangleArea 3 4 5)    -- Expected output: 6.0

    putStrLn "\nArea of triangle with sides 7, 8, 9:"
    print (triangleArea 7 8 9)    -- Expected output: approx. 26.83
```

---

### 🧠 Explanation:

- **Heron’s formula** is a way to calculate the area of a triangle when you know all three side lengths:
  
  \[
  s = \frac{a + b + c}{2}
  \]
  
  \[
  \text{Area} = \sqrt{s(s - a)(s - b)(s - c)}
  \]

- In Haskell:
  - `let s = ...` binds the semi-perimeter.
  - `sqrt` is used for square root.
  - We apply the formula directly inside the function.

---



