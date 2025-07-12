HC11T1: Create a WeAccept instance for the Box type and write a function that returns a list of accepted boxes.

---



```haskell
-- Define the Box type
data Box a = Empty | Has a
    deriving (Show, Eq)

-- Define the WeAccept type class
class WeAccept a where
    isAccepted :: a -> Bool

-- Make Box an instance of WeAccept
instance WeAccept (Box a) where
    isAccepted (Has _) = True
    isAccepted Empty   = False

-- Function to return only accepted boxes
acceptedBoxes :: [Box a] -> [Box a]
acceptedBoxes = filter isAccepted

-- Example usage
main :: IO ()
main = do
    let boxes = [Empty, Has 1, Empty, Has 2, Has 3]
    print $ acceptedBoxes boxes
```

---

### 🧠 Explanation

- **`Box a`**: A simple container that is either `Empty` or contains a value via `Has a`.

- **`WeAccept a` type class**:  
  - Defines a method `isAccepted` that decides acceptance.
  - `WeAccept (Box a)` checks whether a box is non-empty (`Has _`).

- **`acceptedBoxes` function**:  
  - Takes a list of boxes and filters out only those that are accepted using `isAccepted`.

