HC11T10: Implement a function sortContainers that sorts a list of containers using the derived Ord instance.

Here’s an example using the `Box` type:

---



```haskell
import Data.List (sort)

-- Define the Box type
data Box a = Empty | Has a
    deriving (Show, Eq, Ord)

-- Function to sort a list of Box values
sortContainers :: Ord a => [Box a] -> [Box a]
sortContainers = sort

-- Example usage
main :: IO ()
main = do
    let boxes = [Has 10, Empty, Has 7, Empty, Has 42]
    print $ sortContainers boxes
```

---

### 🧠 Explanation

- **Ord Instance for `Box`**:  
  Since we’ve derived `Ord`, Haskell will compare:
  - `Empty < Has x` for any `x`.
  - Between `Has x` and `Has y`, it uses `compare x y`.

- **sortContainers**:  
  - Uses `sort` from `Data.List`, which relies on the `Ord` instance.
  - It's polymorphic: works for any `[Box a]` where `a` has `Ord`.



