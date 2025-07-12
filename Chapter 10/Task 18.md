HC11T8: Derive the Eq and Ord instances for the PaymentMethod and test comparisons.
---


```haskell
-- Define PaymentMethod with automatic Eq and Ord instances
data PaymentMethod = Cash | Card | Crypto
    deriving (Show, Eq, Ord)

-- Example usage
main :: IO ()
main = do
    let pay1 = Cash
    let pay2 = Card
    let pay3 = Crypto

    print $ pay1 == pay2       -- False
    print $ pay2 == Card       -- True
    print $ pay1 < pay2        -- True (Cash < Card)
    print $ pay3 > pay1        -- True (Crypto > Cash)
    print $ min pay1 pay3      -- Cash
    print $ max pay2 pay3      -- Crypto
```

---

### 🧠 Explanation

- **`deriving (Show, Eq, Ord)`**:  
  Automatically generates:
  - `Eq`: so you can compare equality like `==`.
  - `Ord`: so you can do ordering comparisons like `<`, `>`, `min`, `max`.

- **Order of Constructors Matters**:  
  Haskell uses **constructor order** to determine `Ord`.  
  That means:
  ```
  Cash   < Card   < Crypto
  ```

