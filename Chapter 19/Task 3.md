HC19T3: Define a function safeProduct that calculates the product of a list of Maybe Int values, returning Nothing if any value is Nothing.
---


```haskell
import Control.Applicative (liftA2)

-- Function to safely calculate the product of a list of Maybe Int
safeProduct :: [Maybe Int] -> Maybe Int
safeProduct = fmap product . sequenceA

-- Example usage
main :: IO ()
main = do
    let list1 = [Just 2, Just 3, Just 4]
    let list2 = [Just 2, Nothing, Just 4]

    putStrLn "🧮 Safe product of Maybe Int list:"
    print $ safeProduct list1   -- Just 24
    print $ safeProduct list2   -- Nothing
```

---

### 🧠 Explanation

- **`sequenceA :: [Maybe a] -> Maybe [a]`**:
  - Converts a list of `Maybe` values into a single `Maybe` containing a list — but only if all elements are `Just`.
  - If any element is `Nothing`, the result is `Nothing`.

- **`fmap product`**:
  - Applies the `product` function to the inner list if it's present.

So the full expression:
```haskell
fmap product . sequenceA
```
means: “If all values are present, multiply them; otherwise, return `Nothing`.”

---

