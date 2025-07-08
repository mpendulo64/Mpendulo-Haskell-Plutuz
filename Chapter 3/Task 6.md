HC3T6 - Advanced Task 6: Check leap year using if-then-else

```haskell
-- Function to determine whether a year is a leap year
isLeapYear :: Int -> Bool
isLeapYear year =
    if year `mod` 400 == 0 then True
    else if year `mod` 100 == 0 then False
    else if year `mod` 4 == 0 then True
    else False

-- Test cases
main :: IO ()
main = do
    putStrLn $ "Year 2000 is a leap year: " ++ show (isLeapYear 2000)  -- True
    putStrLn $ "Year 1900 is a leap year: " ++ show (isLeapYear 1900)  -- False
    putStrLn $ "Year 2024 is a leap year: " ++ show (isLeapYear 2024)  -- True
```

---

### 🧠 Explanation

The leap year rules according to the Gregorian calendar are:

- **Divisible by 400** → leap year ✅
- **Divisible by 100 but not 400** → not a leap year ❌
- **Divisible by 4** → leap year ✅
- **Otherwise** → not a leap year ❌

In this code:

- We use the modulo operator (`mod`) to check divisibility.
- Each condition is handled explicitly using `if`, `else if`, and `else`.

---

### ✅ Output

When you run this program, it will print:

```
Year 2000 is a leap year: True
Year 1900 is a leap year: False
Year 2024 is a leap year: True
```




