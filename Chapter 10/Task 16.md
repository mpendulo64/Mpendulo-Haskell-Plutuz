HC11T6: Define a type class AdvancedEq that extends Eq and adds a method compareEquality, then implement it for the Blockchain type.

You're asking for:

1. A type class `AdvancedEq` that **extends** `Eq`.
2. It should add a method `compareEquality :: a -> a -> Bool`.
3. An instance implementation for a custom `Blockchain` type.

---



```haskell
-- Define the Blockchain type
data Blockchain = Blockchain
    { name       :: String
    , blockCount :: Int
    } deriving Show

-- Implement Eq for Blockchain
instance Eq Blockchain where
    (Blockchain name1 blocks1) == (Blockchain name2 blocks2) =
        name1 == name2 && blocks1 == blocks2

-- Define AdvancedEq as a subclass of Eq
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> Bool

-- Implement AdvancedEq for Blockchain
instance AdvancedEq Blockchain where
    compareEquality b1 b2
        | b1 == b2 = True  -- strict equality
        | blockCount b1 == blockCount b2 = True  -- fallback equality
        | otherwise = False
```

---

### 🧠 Explanation

- **`Eq Blockchain`**:  
  The regular equality compares both `name` and `blockCount`.

- **`AdvancedEq a`**:  
  A type class that builds on `Eq`, requiring an extra method `compareEquality`.  
  The `Eq a =>` constraint ensures all `AdvancedEq` types must first be instances of `Eq`.

- **`compareEquality` for Blockchain**:  
  - First checks standard equality using `==`.  
  - If not equal, falls back to comparing just `blockCount`.  
  - You could add even more flexible matching logic later!

---

