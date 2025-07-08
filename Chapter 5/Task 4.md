HC5T4: Using Lambda Functions

---


```haskell
-- Lambda version of the biggerThan10 function
biggerThan10 :: Int -> Bool
biggerThan10 = \x -> x > 10
```

---

### 🧠 Explanation

- `\x -> x > 10` is a lambda function — an anonymous function that takes an argument `x` and returns `True` if `x > 10`, otherwise `False`.
- `biggerThan10 = \x -> x > 10` assigns this lambda to the name `biggerThan10`, making it behave just like a regular named function.
- The type signature `Int -> Bool` means it takes an integer and returns a boolean.

---



```haskell
*Main> biggerThan10 5
False

*Main> biggerThan10 15
True
```

