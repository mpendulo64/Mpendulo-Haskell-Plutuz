HC5T5: Partial Application

---



```haskell
-- Function that multiplies any number by 5 using partial application
multiplyByFive :: Num a => a -> a
multiplyByFive = (* 5)
```

---

### 🧠 Explanation

- `multiplyByFive :: Num a => a -> a`:  
  This function works for any numeric type (`Int`, `Float`, `Double`, etc.) thanks to the `Num a` type class constraint.
  
- `(* 5)`:  
  This is partial application of the multiplication operator `(*)`.  
  In Haskell, operators are functions too, so `(* 5)` is a function that takes one argument and multiplies it by 5.

- This is equivalent to writing:
  ```haskell
  multiplyByFive x = x * 5
  ```
  But the partial application version is more concise and idiomatic.



```haskell
*Main> multiplyByFive 3
15

*Main> multiplyByFive 7.2
36.0
```

