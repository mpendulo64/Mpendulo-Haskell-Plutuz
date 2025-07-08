HC1T5 - Task 5: Laziness in Haskell

* The infinite list starts at `0` and increments by 2 (i.e., even numbers).
* You can still extract the first `n` values using `take`.

---

### ✅ **Haskell Code Example**

```haskell
-- Infinite list of even numbers starting from 0
infiniteNumbers :: [Int]
infiniteNumbers = [0,2..]

-- Function to take the first n elements
takeN :: Int -> [Int]
takeN n = take n infiniteNumbers

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "How many even numbers would you like?"
    input <- getLine
    let n = read input :: Int
        result = takeN n
    putStrLn "The first even numbers are:"
    print result
```

---

### ▶️ Example Run

```
How many even numbers would you like?
6
The first even numbers are:
[0,2,4,6,8,10]
```

---





