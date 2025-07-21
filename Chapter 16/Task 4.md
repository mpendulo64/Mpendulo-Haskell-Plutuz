HC16T4: Implement a function that filters only even numbers from a list.
---



```haskell
-- Function that filters only even numbers from a list
filterEvenNumbers :: [Int] -> [Int]
filterEvenNumbers xs = filter even xs

-- Main function to demonstrate usage
main :: IO ()
main = do
    let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    let evens = filterEvenNumbers numbers
    putStrLn $ "✅ Even numbers: " ++ show evens
```

---

### 🧠 Explanation

- **`filterEvenNumbers :: [Int] -> [Int]`**  
  Declares a function that takes a list of integers and returns only the even ones.

- **`filter even xs`**  
  Uses the `filter` function with the built-in predicate `even`, which checks whether a number is divisible by 2.

- **`main`**  
  - Defines a sample list of integers.  
  - Calls `filterEvenNumbers` to extract the even numbers.  
  - Prints the result.

---

