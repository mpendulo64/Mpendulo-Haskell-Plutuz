HC10T7: Create a type class Convertible with convert :: a -> b and implement it for converting PaymentMethod to String.

---



```haskell
{-# LANGUAGE MultiParamTypeClasses #-}
{-# LANGUAGE FunctionalDependencies #-}

-- Define the PaymentMethod type
data PaymentMethod = Cash | Card | Crypto
    deriving Show

-- Define the Convertible type class with a functional dependency
class Convertible a b | a -> b where
    convert :: a -> b

-- Instance to convert PaymentMethod to String
instance Convertible PaymentMethod String where
    convert Cash   = "Paid with cash"
    convert Card   = "Paid using card"
    convert Crypto = "Paid via cryptocurrency"

-- Example usage
main :: IO ()
main = do
    print $ convert Cash
    print $ convert Card
    print $ convert Crypto
```

---

### 🧠 Explanation

- **MultiParamTypeClasses**:  
  Allows a type class to take more than one type parameter (`a` and `b`).

- **FunctionalDependencies (`| a -> b`)**:  
  States that for each source type `a`, there is exactly one target type `b`.  
  This helps the compiler infer what `b` should be when you call `convert`.

- **Instance for `PaymentMethod` → `String`**:  
  Implements custom conversion logic for each constructor.

- **Output**:
  ```
  "Paid with cash"
  "Paid using card"
  "Paid via cryptocurrency"
  ```

---

