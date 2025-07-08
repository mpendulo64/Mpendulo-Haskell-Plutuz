HC1T7 - Task 7: Converting Fahrenheit to Celsius

---
```haskell
-- Define the fToC function
fToC :: Floating a => a -> a
fToC f = (f - 32) * 5 / 9

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "Enter temperature in Fahrenheit:"
    input <- getLine
    let fahrenheit = read input :: Double
        celsius = fToC fahrenheit
    putStrLn ("Temperature in Celsius: " ++ show celsius)
```

---

### 🔁 Example Run

```
Enter temperature in Fahrenheit:
98.6
Temperature in Celsius: 37.0
```

---

### 📌 Notes:

* The formula used is: `C = (F - 32) × 5 / 9`
* The function is **pure** and works with any `Floating` type like `Float` or `Double`.
* This code will run correctly in GHC or GHCi.



