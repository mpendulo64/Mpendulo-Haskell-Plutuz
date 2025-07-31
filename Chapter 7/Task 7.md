HC17T7: Implement a function multiplyProducts that takes a list of Product values and returns the combined result using mconcat.
---



```haskell
import Data.Monoid (Product(..))

-- Multiply all values wrapped in Product using mconcat
multiplyProducts :: [Product Int] -> Product Int
multiplyProducts = mconcat

-- Main function to demonstrate usage
main :: IO ()
main = do
    let numbers = [Product 2, Product 3, Product 4]
    let result = multiplyProducts numbers
    putStrLn $ "🧮 Product of [2, 3, 4] = " ++ show (getProduct result)
```

---

### 🧠 Explanation

- **`Product a`**: A wrapper type from `Data.Monoid` for combining values multiplicatively.
- **`Semigroup instance`**: Combines two `Product` values using `(*)`.
- **`Monoid instance`**:
  - Identity element is `Product 1`, so multiplying by identity doesn’t change the result.
- **`multiplyProducts`**:
  - Uses `mconcat` to multiply a list of `Product` values.

- **`getProduct`**:
  - Extracts the raw numeric result from the `Product` wrapper.

---

