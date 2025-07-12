HC8T2: Define a new type PaymentMethod with the constructors Cash, Card, and Cryptocurrency
```haskell
-- Define PaymentMethod as a custom data type
data PaymentMethod = Cash | Card | Cryptocurrency
    deriving Show

-- Define a Person type with name, address, and payment method
data Person = Person
    { name          :: String
    , address       :: (String, Int)
    , paymentMethod :: PaymentMethod
    } deriving Show

-- Create a person named Bob who pays with Cash
bob :: Person
bob = Person
    { name = "Bob"
    , address = ("123 Main Street", 4567)
    , paymentMethod = Cash
    }

-- Example usage in main
main :: IO ()
main = print bob
```

### 🧠 Explanation:

- **`data PaymentMethod = Cash | Card | Cryptocurrency`** defines an algebraic data type with three constructors. You can pattern match against this easily.
- **`data Person = Person { ... }`** uses _record syntax_ to define fields with labels, which makes construction and access more readable.
- `address` is a **tuple** of a `String` (street name) and an `Int` (postal code or house number).
- The `deriving Show` clause allows printing `bob` in the console without extra code.






