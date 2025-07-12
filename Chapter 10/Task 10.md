HC10T10: Create a type class Concatenatable with a function concatWith :: a -> a -> a. Implement it for the type [Char].
---



```haskell
-- Define the Concatenatable type class
class Concatenatable a where
    concatWith :: a -> a -> a

-- Implement Concatenatable for String (i.e., [Char])
instance Concatenatable [Char] where
    concatWith s1 s2 = s1 ++ s2

-- Example usage
main :: IO ()
main = do
    let hello = "Hello, "
    let name  = "Mpendulo!"
    putStrLn $ concatWith hello name  -- Output: Hello, Mpendulo!
```

---

### 🧠 Explanation

- **`class Concatenatable a where`**  
  Declares a new type class for types that support merging or combining.

- **`concatWith :: a -> a -> a`**  
  Specifies the method that takes two values of type `a` and returns their concatenation.

- **`instance Concatenatable [Char]`**  
  Implements the method specifically for strings. Uses the built-in `(++)` operator to join them.

- **Usage in `main`**:  
  Combines `"Hello, "` and `"Mpendulo!"` into a single string.

---


