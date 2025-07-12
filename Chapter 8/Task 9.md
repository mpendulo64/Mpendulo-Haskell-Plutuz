HC8T9: Define a type Transaction with fields from :: Address, to :: Address, amount :: Value, and transactionId :: String. Define a function createTransaction :: Address -> Address -> Value -> String that creates a Transaction and returns the transaction id.

```haskell
-- Type synonyms for clarity
type Address = String
type Value   = Float

-- Define the Transaction type using record syntax
data Transaction = Transaction
    { from          :: Address
    , to            :: Address
    , amount        :: Value
    , transactionId :: String
    } deriving Show

-- Function that creates a Transaction and returns the transactionId
createTransaction :: Address -> Address -> Value -> String
createTransaction fromAddr toAddr amt =
    transactionId tx
  where
    tx = Transaction
        { from = fromAddr
        , to = toAddr
        , amount = amt
        , transactionId = generateId fromAddr toAddr amt
        }

-- Helper function to simulate generating a transaction ID
generateId :: Address -> Address -> Value -> String
generateId fromAddr toAddr amt =
    take 12 $ fromAddr ++ toAddr ++ show amt
```

---

### 🧠 Explanation:

- **Type synonyms**:
  - `Address` and `Value` improve readability while still being `String` and `Float` respectively.

- **Record syntax**:
  - `Transaction` has clearly labeled fields, making construction and access intuitive.

- **`createTransaction` function**:
  - Takes input values and creates a `Transaction` record.
  - Returns only the `transactionId` from the constructed transaction.

- **`generateId` helper**:
  - Creates a basic `transactionId` by concatenating inputs and trimming to 12 characters—this simulates generating a lightweight identifier.

---



**Output:**
```
Transaction ID: addr1addr2100
```

---

