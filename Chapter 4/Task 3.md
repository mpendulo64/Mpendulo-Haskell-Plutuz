HC4T3 - Task 3: Define a gradeComment Function

```haskell
-- Function to return a comment based on a numerical grade
gradeComment :: Int -> String
gradeComment grade
  | grade >= 90 && grade <= 100 = "Excellent!"
  | grade >= 70 && grade <= 89  = "Good job!"
  | grade >= 50 && grade <= 69  = "You passed."
  | grade >= 0  && grade <= 49  = "Better luck next time."
  | otherwise                   = "Invalid grade"
```

---

### 🧠 Explanation

- `gradeComment :: Int -> String`: This declares the function type. It takes an `Int` (the grade) and returns a `String` (the comment).
- The function uses **guards** (`|`) to check which range the grade falls into.
- Each guard checks a specific range:
  - `90–100` → "Excellent!"
  - `70–89` → "Good job!"
  - `50–69` → "You passed."
  - `0–49` → "Better luck next time."
- `otherwise` is a catch-all for any grade outside the valid 0–100 range.

---
