-- HC6T8: Implement a function that filters all even numbers from a list.

```haskell
-- Filter even numbers from a list
filterEvens :: [Int] -> [Int]
filterEvens xs = filter even xs
```

### 🧠 Explanation:

- **`filter`** is a higher-order function that takes a predicate and a list, and returns a new list of elements that satisfy the predicate.
- **`even`** is a built-in predicate function that checks if a number is divisible by 2.
- So, `filter even xs` returns a list containing only the elements in `xs` that are even.


