HC18T7: Define a function fmapTuple that applies a function to the second element of a tuple (a, b) using the Functor instance of (,) a.
---

### 🧩 Key Insight

In Haskell, the type `(,) a` — that is, a tuple where the first element is fixed — is a Functor **over the second element**. So `fmap` will apply a function to the second element, leaving the first untouched.

---



```haskell
-- Function that applies a transformation to the second element of a tuple
fmapTuple :: (b -> c) -> (a, b) -> (a, c)
fmapTuple = fmap

-- Example usage
main :: IO ()
main = do
    let pair1 = ("score", 42)
    let pair2 = ("level", 7)

    putStrLn "🎯 Applying (+1) to second elements of tuples:"
    print $ fmapTuple (+1) pair1   -- ("score", 43)
    print $ fmapTuple (*2) pair2   -- ("level", 14)
```

---

### 🧠 Explanation

- **Type `(a, b)`** is treated as a Functor over `b` when partially applied: `(,) a`.
- **`fmap`** applies the function to the second element (`b`) and leaves the first (`a`) unchanged.
- **`fmapTuple`** is just `fmap` specialized to this context.

---
