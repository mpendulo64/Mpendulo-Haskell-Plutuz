-- HC6T1: Implement a recursive function to compute the factorial of a number
```haskell
-- Recursive factorial function
factorial :: Integer -> Integer
factorial 0 = 1                      -- Base case: factorial of 0 is 1
factorial n = n * factorial (n - 1) -- Recursive case

-- Main function to test factorial
main :: IO ()
main = do
    putStrLn "Enter a non-negative integer:"
    input <- getLine
    let number = read input :: Integer
    if number < 0
        then putStrLn "Factorial is not defined for negative numbers."
        else putStrLn $ "Factorial of " ++ show number ++ " is " ++ show (factorial number)
```

### Explanation

* The function `factorial` takes an `Integer` and returns an `Integer`.
* **Base case:** When the input is 0, it returns 1.
* **Recursive case:** For any positive integer `n`, it multiplies `n` by `factorial (n - 1)`.
* The recursion continues until it reaches the base case.
* The `main` function reads user input, validates it, and prints the factorial.

---

Let me know if you want me to explain tail recursion or provide other variations!
