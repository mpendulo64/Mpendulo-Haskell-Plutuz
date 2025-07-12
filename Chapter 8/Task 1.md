HC8T1: Create a type synonym called Address for String and a type synonym called Value for Int.
```haskell
-- Define types for clarity
type Address = String
type Value   = String

-- Generate a transaction string from two addresses and a value
generateTx :: Address -> Address -> Value -> String
generateTx fromAddr toAddr val =
    "From: " ++ fromAddr ++ " | To: " ++ toAddr ++ " | Value: " ++ val
```

### 🧠 Explanation:

- **Type Aliases**:
  - `type Address = String` and `type Value = String` make the function signature more descriptive while still working with plain strings.
- **Function Logic**:
  - `generateTx` takes three arguments: `fromAddr`, `toAddr`, and `val`.
  - It constructs a single string using string concatenation (`++`), adding labels like `"From:"` and separators to format the output clearly.

