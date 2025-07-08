HC1T3 - Task 3: Checking if a Number is Greater than 18

```haskell
-- Define the greaterThan18 function
greaterThan18 :: (Ord a, Num a) => a -> Bool
greaterThan18 x = x > 18

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "Enter a number:"
    input <- getLine
    let number = read input :: Int
    if greaterThan18 number
        then putStrLn "The number is greater than 18."
        else putStrLn "The number is not greater than 18."
```

### Explanation:

* `greaterThan18` is a pure function that returns `True` if the input is greater than 18.
* The `main` function takes user input, converts it to an integer, and checks it using `greaterThan18`.

### Example Run:

```
Enter a number:
25
The number is greater than 18.
```




