HC10T8: Define a subclass AdvancedEq of Eq with an additional method compareEquality :: a -> a -> Bool.
---



```haskell
-- Define the AdvancedEq type class as a subclass of Eq
class Eq a => AdvancedEq a where
    compareEquality :: a -> a -> Bool

-- Example type: Blockchain
data Blockchain = Blockchain
    { name       :: String
    , blockCount :: Int
    } deriving Show

-- Make Blockchain an Eq instance
instance Eq Blockchain where
    b1 == b2 = name b1 == name b2 && blockCount b1 == blockCount b2

-- Make Blockchain an AdvancedEq instance
instance AdvancedEq Blockchain where
    compareEquality b1 b2 =
        if b1 == b2
        then True
        else blockCount b1 == blockCount b2  -- fallback equality logic
```

---

### 🧠 Explanation

- **`class Eq a => AdvancedEq a`**  
  Declares `AdvancedEq` as a subclass — so it extends `Eq`.  
  You can safely use `==` inside `compareEquality`.

- **Eq instance for `Blockchain`**  
  Implements standard equality by comparing both `name` and `blockCount`.

- **AdvancedEq instance for `Blockchain`**  
  Defines `compareEquality` such that:
  - If two blockchains are exactly equal, return `True`.
  - Otherwise, it checks if their `blockCount` is equal as a secondary criterion — a more relaxed equivalence.

---





