HC18T4: Implement a function mapToBits to convert a list of Booleans to characters '1' or '0' using fmap.
---

```haskell
-- Function to convert Bool to '1' or '0'
boolToBit :: Bool -> Char
boolToBit True  = '1'
boolToBit False = '0'

-- Function to map a list of Bools to bits using fmap
mapToBits :: [Bool] -> [Char]
mapToBits = fmap boolToBit

-- Example usage
main :: IO ()
main = do
    let bools = [True, False, True, True, False]
    putStrLn "🔢 Original Booleans:"
    print bools

    let bits = mapToBits bools
    putStrLn "\n💡 Converted to Bits:"
    print bits
```

---

### 🧠 Explanation

- **`boolToBit`**: Converts `True` to `'1'` and `False` to `'0'`.
- **`mapToBits`**:
  - Uses `fmap` to apply `boolToBit` to each element of the list.
  - Since lists are Functors, `fmap` works just like `map`.
- **`main`**:
  - Demonstrates the transformation with a sample list.

---

