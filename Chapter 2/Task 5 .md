HC2T5 - Task 5: Defining and Using Functions

```haskell
-- Function to calculate the area of a circle
circleArea :: Float -> Float
circleArea radius = pi * radius * radius

-- Function to find the maximum of three integers
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree x y z = max x (max y z)

main :: IO ()
main = do
    -- Testing circleArea
    putStrLn "Testing circleArea:"
    print (circleArea 5.0)   -- Output should be 78.53982
    print (circleArea 2.5)   -- Output should be 19.634954

    -- Testing maxOfThree
    putStrLn "\nTesting maxOfThree:"
    print (maxOfThree 3 7 5) -- Output: 7
    print (maxOfThree 10 2 8) -- Output: 10
```

### 🔍 What’s happening here:

- `circleArea` uses the built-in `pi` constant and the formula \( \pi r^2 \).
- `maxOfThree` uses the built-in `max` function twice to nest comparisons.
- In `main`, we test the functions with various inputs and print the results.





