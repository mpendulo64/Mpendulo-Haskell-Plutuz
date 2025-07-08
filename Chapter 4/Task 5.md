HC4T5 - Task 5: Add a Catch-All Pattern with a Custom Message

---

### ✅ Updated Haskell Code

```haskell
-- Function to check for special birthdays and include age in the default case
specialBirthday :: Int -> String
specialBirthday 1  = "You're celebrating a special birthday!"
specialBirthday 18 = "You're celebrating a special birthday!"
specialBirthday age = "You're " ++ show age ++ " years old. Just another year older."
```

---

### 🧠 Explanation

- `specialBirthday 1` and `specialBirthday 18`: These are still treated as special cases.
- `specialBirthday age`: This pattern matches any other age and binds it to the variable `age`.
- `"You're " ++ show age ++ " years old..."`: We use `show` to convert the integer `age` into a string so it can be concatenated into the message.

---

