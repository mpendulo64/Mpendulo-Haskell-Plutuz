HC5T9: Higher-Order Function to Transform a List

---

```haskell
-- Applies a given function twice to every element in a list
transformList :: (a -> a) -> [a] -> [a]
transformList f = map (f . f)
```

---

### 🧠 Explanation

- `transformList :: (a -> a) -> [a] -> [a]`:  
  This function takes:
  - A function `f` that transforms a value of type `a`
  - A list of values of type `[a]`
  - And returns a new list where `f` has been applied twice to each element.

- `map (f . f)`:  
  - `f . f` means function composition — it creates a new function that applies `f` twice:  
    `(f . f) x = f (f x)`
  - `map (f . f)` applies this composed function to every element in the list.

---

```haskell
*Main> transformList (+1) [1,2,3]
[3,4,5]  -- because (+1) applied twice: 1→2→3, 2→3→4, 3→4→5

*Main> transformList (*2) [1,2,3]
[4,8,12]  -- because (*2) applied twice: 1→2→4, 2→4→8, 3→6→12
