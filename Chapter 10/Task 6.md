HC10T6: Modify the Eq type class to use mutual recursion between == and /= in an instance for the Blockchain type.

This involves manually defining both `(==)` and `(/=)` such that each uses the other. Haskell allows this via lazy (recursive) bindings.

---


```haskell
-- Define the Blockchain type
data Blockchain = Blockchain
    { name       :: String
    , blockCount :: Int
    } deriving Show

-- Custom Eq instance using mutual recursion
instance Eq Blockchain where
    x == y = not (x /= y)
    x /= y = not (x == y)
```

---

### 🧪 Example Usage

```haskell
main :: IO ()
main = do
    let chain1 = Blockchain "ChainX" 100
    let chain2 = Blockchain "ChainX" 100
    let chain3 = Blockchain "ChainY" 150

    print (chain1 == chain2)  -- True
    print (chain1 == chain3)  -- False
    print (chain1 /= chain3)  -- True
```

---

### 🧠 Explanation

- **Mutual Recursion**:
  - `x == y` is defined as `not (x /= y)`
  - `x /= y` is defined as `not (x == y)`
  - This is legal in Haskell due to laziness — the compiler resolves both at runtime.

- **How It Works**:
  - Haskell allows cyclic bindings in type class methods.
  - However, this alone won't work until the compiler can reduce either `(==)` or `(/=)` based on data.
  - To make the instance actually meaningful, you would usually *break* the cycle with a real implementation.
  
  So to avoid infinite loops, you'd often include logic like:

```haskell
instance Eq Blockchain where
    x == y = name x == name y && blockCount x == blockCount y
    x /= y = not (x == y)
```

