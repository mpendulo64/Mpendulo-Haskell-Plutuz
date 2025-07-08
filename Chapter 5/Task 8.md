HC5T8: Point-Free Style

---

```haskell
-- Point-free version of addFive
addFive :: Num a => a -> a
addFive = (+ 5)
```

---

### 🧠 Explanation

- Original version:
  ```haskell
  addFive x = x + 5
  ```
  This explicitly takes an argument `x` and adds 5 to it.

- Point-free version:
  ```haskell
  addFive = (+ 5)
  ```
  This uses partial application of the `(+)` operator. In Haskell, operators are functions, so `(+ 5)` is a function that takes a number and adds 5 to it.

- The type signature `Num a => a -> a` means it works for any numeric type (like `Int`, `Float`, etc.).

---

```haskell
*Main> addFive 10
15

*Main> addFive (-2)
3
```
