HC12T7
Create a function calculateCircleArea that calculates the area of a circle given its radius. The main function should demonstrate its usage.
\[
\text{Area} = \pi r^2
\]

We’ll use `Prelude.pi` for π and demonstrate the function in `main`.

---



```haskell
-- Function to calculate the area of a circle
calculateCircleArea :: Float -> Float
calculateCircleArea radius = pi * radius * radius

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🧮 Enter the radius of the circle:"
    input <- getLine
    let radius = read input :: Float
    let area = calculateCircleArea radius
    putStrLn $ "📏 The area of the circle is: " ++ show area
```

---

### 🧠 Explanation

- **`calculateCircleArea :: Float -> Float`**  
  - Takes a `Float` representing the radius.
  - Returns the area computed with `pi * r²`.

- **`read input :: Float`**  
  - Converts the user's input string into a `Float`.

- **`show area`**  
  - Converts the result back into a string so it can be displayed.

- **`putStrLn`**  
  - Prints the prompt and final output with friendly formatting.

---

