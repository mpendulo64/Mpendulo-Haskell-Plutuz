HC1T6 - Task 6: Using Type Signatures

```haskell
-- Define the addNumbers function
addNumbers :: Int -> Int -> Int
addNumbers x y = x + y

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "Enter the first number:"
    input1 <- getLine
    putStrLn "Enter the second number:"
    input2 <- getLine
    let num1 = read input1 :: Int
        num2 = read input2 :: Int
        result = addNumbers num1 num2
    putStrLn ("The sum is: " ++ show result)
```

---

### ✅ Example Run:

```
Enter the first number:
7
Enter the second number:
5
The sum is: 12
```





