HC3T8 - Advanced Task 8: Calculate BMI and return category using where

```haskell
-- Function to classify BMI using guards and where binding
bmiCategory :: Float -> Float -> String
bmiCategory weight height
    | bmi < 18.5               = "Underweight"
    | bmi >= 18.5 && bmi <= 24.9 = "Normal"
    | bmi >= 25   && bmi <= 29.9 = "Overweight"
    | bmi == 30                = "Obese"
    | bmi > 30                 = "Obese"
    | otherwise                = "Invalid BMI"
    where bmi = weight / (height ^ 2)

-- Test cases
main :: IO ()
main = do
    putStrLn $ "BMI for 70kg and 1.75m: " ++ bmiCategory 70 1.75  -- Expected: "Normal"
    putStrLn $ "BMI for 90kg and 1.8m: "  ++ bmiCategory 90 1.8   -- Expected: "Overweight"
```

---

### 🧠 Explanation:

- **`bmi = weight / (height ^ 2)`**: This is stored in the `where` clause so it's computed once and reused in the guards.
- **Guards (`|`)**: These check the value of `bmi` and return the appropriate category string.
- We also include a final guard (`| otherwise`) to catch any unexpected edge cases.
- **The result is a pure function** that neatly separates the logic from the computation.

---

### ✅ Output:

```
BMI for 70kg and 1.75m: Normal
BMI for 90kg and 1.8m: Overweight
```

