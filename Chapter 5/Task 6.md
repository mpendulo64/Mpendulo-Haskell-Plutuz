HC5T6: Function Composition

---

```haskell
-- Function that squares numbers and filters only the even results using function composition
evenSquares :: [Int] -> [Int]
evenSquares = filter even . map (^2)
```

---

### 🧠 Explanation

- `evenSquares :: [Int] -> [Int]`:  
  This function takes a list of integers and returns a list of even squares.

- `map (^2)`:  
  This maps the squaring function `(^2)` over the list — squaring each number.

- `filter even`:  
  This filters the list to keep only even numbers.

- `filter even . map (^2)`:  
  This is function composition. It means:  
  “First square every number in the list, then filter the result to keep only the even ones.”

- Function composition `(.)` in Haskell is defined as:
  ```haskell
  (f . g) x = f (g x)
  ```

---



```haskell
*Main> evenSquares [1..10]
[4,16,36,64,100]

*Main> evenSquares [3,5,7]
[]
```

