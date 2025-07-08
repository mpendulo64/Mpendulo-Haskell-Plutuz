HC3T1 - Task 1: Check if a number is positive, negative, or zero

```haskell
-- Function that checks if a number is positive, negative, or zero
checkNumber :: Int -> String
checkNumber n =
    if n > 0 then "Positive"
    else if n < 0 then "Negative"
    else "Zero"

-- Testing the function with example values
main :: IO ()
main = do
    print (checkNumber 5)    -- Output: "Positive"
    print (checkNumber (-3)) -- Output: "Negative"
    print (checkNumber 0)    -- Output: "Zero"
```

### 🧠 How it works:

- `checkNumber` takes an `Int` and returns a `String`.
- It uses an `if-then-else` chain:
  - If the number is greater than 0, it returns `"Positive"`.
  - If the number is less than 0, it returns `"Negative"`.
  - Otherwise, it must be 0, so it returns `"Zero"'.



