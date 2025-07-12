HC11T4: Implement the Container type class for the Present type.

---



```haskell
-- Define the Present type
data Present a = EmptyWrap | Wrapped a
    deriving (Show, Eq)

-- Define the Container type class
class Container c where
    isEmpty  :: c a -> Bool
    contains :: Eq a => c a -> a -> Bool
    replace  :: c a -> a -> c a

-- Implement Container for Present
instance Container Present where
    isEmpty EmptyWrap      = True
    isEmpty (Wrapped _)    = False

    contains EmptyWrap _   = False
    contains (Wrapped x) y = x == y

    replace _ newItem      = Wrapped newItem

-- Example usage
main :: IO ()
main = do
    let p1 = EmptyWrap :: Present String
    let p2 = Wrapped "Haskell"

    print $ isEmpty p1             -- True
    print $ isEmpty p2             -- False
    print $ contains p2 "Haskell"  -- True
    print $ contains p2 "Rust"     -- False
    print $ replace p1 "Gift"      -- Wrapped "Gift"
    print $ replace p2 "Sticker"   -- Wrapped "Sticker"
```

---

### 🧠 Explanation

- **`data Present a`**:  
  - `EmptyWrap`: represents a present with nothing inside.
  - `Wrapped a`: contains a value of type `a`, like a thoughtful gift.

- **`Container` Type Class**:  
  - `isEmpty`: checks whether the present is empty.
  - `contains`: verifies whether a specific value is wrapped.
  - `replace`: swaps out the current content with something new.

- **Instance Logic**:
  - Follows the same structure as `Box`, but with thematic naming.
  - Enables composable use across different container-like types.

---

