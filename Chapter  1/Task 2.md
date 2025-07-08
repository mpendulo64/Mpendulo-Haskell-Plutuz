HC1T2 - Task 2: Pure Function Example

```haskell
-- Define the circleArea function
circleArea :: Floating a => a -> a
circleArea r = pi * r * r

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "Enter the radius of the circle:"
    input <- getLine
    let radius = read input :: Double
        area = circleArea radius
    putStrLn ("The area of the circle is: " ++ show area)
```

### Explanation:

* `circleArea :: Floating a => a -> a` — this makes the function work for any floating-point type like `Float` or `Double`.
* It uses the formula: **area = π × r²**
* The `main` function reads user input, applies `circleArea`, and prints the result.

### Example Run:

```
Enter the radius of the circle:
3
The area of the circle is: 28.274333882308138
```




