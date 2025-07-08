HC5T2: Filtering Odd Numbers

---

```haskell
-- Extract all odd numbers from 1 to 30 using filter
oddNumbers :: [Int]
oddNumbers = filter odd [1..30]
```

---

### 🧠 Explanation

- `filter` is a higher-order function that takes:
  - A predicate function (in this case, `odd`)
  - A list (in this case, `[1..30]`, which generates the list `[1,2,3,...,30]`)
- `odd` is a built-in function that returns `True` for odd numbers and `False` for even ones.
- `filter odd [1..30]` returns a new list containing only the elements for which `odd` returns `True`.

---  
*Main> oddNumbers
[1,3,5,7,9,11,13,15,17,19,21,23,25,27,29]

