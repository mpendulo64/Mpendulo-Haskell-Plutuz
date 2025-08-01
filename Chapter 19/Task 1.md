HC19T1: Define an Applicative instance for a custom data type Pair a.
---

### 🧱 Step 1: Define the Data Type

We'll define a simple `Pair` type that holds two values of the same type:

```haskell
-- Custom data type
data Pair a = Pair a a deriving (Show, Eq)
```

---

### 🧠 Step 2: Functor Instance

Before we can define `Applicative`, we need a `Functor` instance:

```haskell
instance Functor Pair where
    fmap f (Pair x y) = Pair (f x) (f y)
```

This applies the function `f` to both elements of the pair.

---

### ✨ Step 3: Applicative Instance

```haskell
instance Applicative Pair where
    pure x = Pair x x
    Pair f g <*> Pair x y = Pair (f x) (g y)
```

#### Explanation:
- **`pure x`**: Wraps a value into a `Pair`, duplicating it.
- **`<*>`**: Applies each function in the first `Pair` to the corresponding value in the second `Pair`.

---
-- Define the Pair type
data Pair a = Pair a a deriving (Show, Eq)

-- Functor instance
instance Functor Pair where
    fmap f (Pair x y) = Pair (f x) (f y)

-- Applicative instance
instance Applicative Pair where
    pure x = Pair x x
    Pair f g <*> Pair x y = Pair (f x) (g y)

-- Example usage
main :: IO ()
main = do
    let pf = Pair (+1) (*2)
    let px = Pair 3 4

    putStrLn "🚀 Applying Pair of functions to Pair of values:"
    print $ pf <*> px         -- Pair 4 8
    print $ pure 5 :: Pair Int -- Pair 5 5
---
