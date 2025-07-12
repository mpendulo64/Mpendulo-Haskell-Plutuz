HC10T3: Define a type class Comparable with a function compareWith :: a -> a -> Ordering. Implement it for Blockchain
```haskell
-- Define a simple Blockchain type with name and block count
data Blockchain = Blockchain
    { chainName   :: String
    , blockCount  :: Int
    } deriving Show

-- Define a type class Comparable
class Comparable a where
    compareWith :: a -> a -> Ordering

-- Implement Comparable for Blockchain
instance Comparable Blockchain where
    compareWith b1 b2 = compare (blockCount b1) (blockCount b2)

-- Example usage
main :: IO ()
main = do
    let chainA = Blockchain "ChainA" 1200
    let chainB = Blockchain "ChainB" 950
    let result = compareWith chainA chainB
    print result  -- Output: GT (since 1200 > 950)
```

---

### 🧠 Explanation

- **`data Blockchain`**:  
  Holds basic info—a name and a number of blocks. You could extend this with value, hash difficulty, or timestamp later.

- **Type class `Comparable`**:  
  Provides a custom comparison method `compareWith :: a -> a -> Ordering`. This gives you flexibility beyond default `Ord`.

- **Instance for `Blockchain`**:  
  Compares blockchains by their `blockCount`. This could easily be adapted to compare by other metrics.

- **`Ordering` type**:  
  - `LT` = Less Than  
  - `GT` = Greater Than  
  - `EQ` = Equal

---

