HC5T1: Using applyTwice

---

```haskell
-- Function that applies a given function three times to an integer
applyThrice :: (Int -> Int) -> Int -> Int
applyThrice f x = f (f (f x))
```

---

### 🧠 Explanation

- `applyThrice :: (Int -> Int) -> Int -> Int`:
  - The function takes two arguments:
    - A function `f` of type `Int -> Int` (a function that takes an `Int` and returns an `Int`)
    - An integer `x`
  - It returns the result of applying `f` to `x` three times: `f (f (f x))`
- This is a classic example of function composition and higher-order functions in Haskell.

---

### 🧪 Example Usage in GHCi

```haskell
*Main> applyThrice (+1) 5
8

*Main> applyThrice (*2) 1
8

*Main> applyThrice (\x -> x * x) 2
256
```

- `(+1)` applied three times to `5`:  
  → `6 → 7 → 8`
- `(*2)` applied three times to `1`:  
  → `2 → 4 → 8`
- `(\x -> x * x)` (square function) applied three times to `2`:  
  → `2² = 4 → 4² = 16 → 16² = 256`

