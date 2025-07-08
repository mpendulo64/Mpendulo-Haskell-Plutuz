HC4T4 - Task 4: Rewrite specialBirthday using Pattern Matching

---

### 🎯 Goal

We want a function that checks if a given age is a "special birthday" — for example:

- Age 1 or 18 → "You're celebrating a special birthday!"
- Any other age → "Just another year older."

---

### ✅ Haskell Code Using Pattern Matching

```haskell
-- Function to check for special birthdays using pattern matching
specialBirthday :: Int -> String
specialBirthday 1  = "You're celebrating a special birthday!"
specialBirthday 18 = "You're celebrating a special birthday!"
specialBirthday _  = "Just another year older."
```

---

### 🧠 Explanation

- `specialBirthday :: Int -> String`: The function takes an `Int` (age) and returns a `String` (message).
- `specialBirthday 1` and `specialBirthday 18`: These are specific patterns that match exactly when the input is 1 or 18.
- `specialBirthday _`: The underscore `_` is a wildcard that matches any other value not previously matched — this is the default case.

---

