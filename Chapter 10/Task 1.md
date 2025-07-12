HC10T1: Define a new type class ShowSimple that requires a function showSimple :: a -> String for simple string conversion. Implement an instance for PaymentMethod type.

---



```haskell
-- Define the PaymentMethod type
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving Show

-- Define the ShowSimple type class
class ShowSimple a where
    showSimple :: a -> String

-- Provide an instance of ShowSimple for PaymentMethod
instance ShowSimple PaymentMethod where
    showSimple Cash          = "Paid with cash"
    showSimple Card          = "Paid using a card"
    showSimple Cryptocurrency = "Paid in cryptocurrency"

-- Example usage
main :: IO ()
main = do
    print $ showSimple Cash
    print $ showSimple Card
    print $ showSimple Cryptocurrency
```

---

### 🧠 Explanation

- **`class ShowSimple a where showSimple :: a -> String`**  
  Declares a new type class for simplified string rendering — like a customized, human-friendly alternative to `Show`.

- **Instance for `PaymentMethod`**:  
  Each constructor (`Cash`, `Card`, `Cryptocurrency`) maps to a readable string.

- **`main` function** demonstrates usage:
  ```haskell
  showSimple Cash          -- "Paid with cash"
  showSimple Card          -- "Paid using a card"
  showSimple Cryptocurrency -- "Paid in cryptocurrency"
  ```

---

