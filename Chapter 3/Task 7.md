HC3T7 - Advanced Task 7: Determine the season based on the month using guards

```haskell
-- Function to map month numbers to seasons using guards
season :: Int -> String
season month
    | month == 12 || month == 1 || month == 2  = "Winter"
    | month >= 3  && month <= 5                = "Spring"
    | month >= 6  && month <= 8                = "Summer"
    | month >= 9  && month <= 11               = "Autumn"
    | otherwise                                = "Invalid month"

-- Testing the function
main :: IO ()
main = do
    putStrLn $ "season 3: " ++ season 3    -- Expected: "Spring"
    putStrLn $ "season 7: " ++ season 7    -- Expected: "Summer"
    putStrLn $ "season 11: " ++ season 11  -- Expected: "Autumn"
```

---

### 🧠 Explanation:

- `season :: Int -> String`: The function takes a number from 1 to 12 and returns the season name as a string.
- **Guards (`|`)** are used to clearly express conditions:
  - Months 12, 1, 2 → `"Winter"`
  - Months 3 to 5   → `"Spring"`
  - Months 6 to 8   → `"Summer"`
  - Months 9 to 11  → `"Autumn"`
- `otherwise` handles unexpected inputs (e.g., 0 or 13).

---

### ✅ Output:

```
season 3: Spring
season 7: Summer
season 11: Autumn
```




