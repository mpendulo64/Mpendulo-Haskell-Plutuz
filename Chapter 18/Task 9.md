HC18T9: Implement the compositionLawCheck function to verify the Functor composition law.
---

### 📜 Functor Composition Law

The composition law states:

> For any Functor `f` and functions `g :: b -> c` and `h :: a -> b`:
>
> \[
> \text{fmap (g . h)} = \text{fmap g . fmap h}
> \]

This ensures that mapping a composed function is the same as mapping each function in sequence.

---



```haskell
-- Function to check the Functor composition law
compositionLawCheck :: (Eq (f c), Functor f) => (b -> c) -> (a -> b) -> f a -> Bool
compositionLawCheck g h x = fmap (g . h) x == (fmap g . fmap h) x

-- Example usage with Maybe and List
main :: IO ()
main = do
    let maybeVal = Just 3
    let listVal  = [1, 2, 3]
    let tupleVal = ("meta", 5)

    let g = (+1)      -- b -> c
    let h = (*2)      -- a -> b

    putStrLn "🔗 Checking Functor composition law:"
    print $ compositionLawCheck g h maybeVal   -- True
    print $ compositionLawCheck g h listVal    -- True
    print $ compositionLawCheck g h tupleVal   -- True
```

---

### 🧠 Explanation

- **`compositionLawCheck g h x`** compares:
  - `fmap (g . h) x` — applying the composed function directly.
  - `(fmap g . fmap h) x` — applying each function in sequence via `fmap`.
- Works for any Functor `f` where equality is defined (`Eq (f c)`).

---

