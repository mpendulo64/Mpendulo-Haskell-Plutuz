HC17T4: Implement the Monoid instance for the Sum newtype, where the identity element is 0.
---


```haskell
-- Define a Sum newtype wrapper
newtype Sum a = Sum { getSum :: a }
    deriving (Eq, Show)

-- Semigroup instance: defines how to combine two Sum values
instance Num a => Semigroup (Sum a) where
    Sum x <> Sum y = Sum (x + y)

-- Monoid instance: identity value is 0
instance Num a => Monoid (Sum a) where
    mempty = Sum 0
    mappend = (<>)

-- Example usage
main :: IO ()
main = do
    let a = Sum 10
    let b = Sum 15
    let c = mempty

    putStrLn $ "🧮 Sum 10 <> Sum 15 = " ++ show (a <> b)
    putStrLn $ "🧮 mempty <> Sum 10 = " ++ show (c <> a)
    putStrLn $ "🧮 Sum 15 <> mempty = " ++ show (b <> c)
```

---

### 🧠 Explanation

- **`newtype Sum a`**: Encapsulates a numeric value `a` so we can define custom `Semigroup` and `Monoid` behavior.
- **Semigroup (`<>`)**: Combines two `Sum` values by adding their contents.
- **Monoid (`mempty`)**: Uses `0` as the identity, so combining with it doesn’t affect the total.
- **Why `newtype`?**: It's efficient and gives semantic meaning to the operation.

---



