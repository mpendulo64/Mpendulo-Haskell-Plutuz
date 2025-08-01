HC18T8: Implement the identityLawCheck function to verify the Functor identity law.
---

### 📜 Functor Identity Law

The identity law states:

> For any Functor `f`, applying `fmap id` should be the same as just using the original functor:
>
> \[
> \text{fmap id} = id
> \]

---



```haskell
-- Function to check the Functor identity law
identityLawCheck :: (Eq (f a), Functor f) => f a -> Bool
identityLawCheck x = fmap id x == x

-- Example usage with Maybe and List
main :: IO ()
main = do
    let maybeVal = Just "hello"
    let listVal  = [1, 2, 3]
    let tupleVal = ("meta", 42)

    putStrLn "🧪 Checking Functor identity law:"
    print $ identityLawCheck maybeVal   -- True
    print $ identityLawCheck listVal    -- True
    print $ identityLawCheck tupleVal   -- True
```

---

### 🧠 Explanation

- **`identityLawCheck`** takes a Functor value `x` and checks if `fmap id x == x`.
- It works for **any Functor** that supports equality (`Eq`) — like `Maybe`, `[]`, and `(,) a`.
- This is a **property test** — useful in both manual checks and property-based testing (e.g. QuickCheck).

---

