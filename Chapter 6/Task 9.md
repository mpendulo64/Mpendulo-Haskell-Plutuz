-- HC6T9: Implement a function that applies a given function to each element of a list (map implementation).

```haskell
-- Apply a given function to each element of a list
myMap :: (a -> b) -> [a] -> [b]
myMap _ []     = []
myMap f (x:xs) = f x : myMap f xs
```

### 🧠 Explanation:

- **Type Signature**:  
  `myMap :: (a -> b) -> [a] -> [b]`  
  This means it takes a function from type `a` to `b`, and applies it to a list of `a`s to produce a list of `b`s.

- **Base Case**:  
  `myMap _ [] = []`  
  If the list is empty, return an empty list—nothing to apply the function to.

- **Recursive Case**:  
  `myMap f (x:xs) = f x : myMap f xs`  
  - Apply the function `f` to the head `x`
  - Use `:` to prepend the result to the recursively mapped tail

