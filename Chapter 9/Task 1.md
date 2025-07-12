HC9T1: Define a Parametric Type Synonym
---


```haskell
-- Define Address as a tuple of (Street Name, Number)
type Address = (String, Int)

-- Define a parametric type synonym Entity
type Entity a = (a, Address)

-- Example usage with different types of entities
company :: Entity String
company = ("TechCorp", ("Silicon Avenue", 42))

person :: Entity (String, Int)
person = (("Alice", 30), ("Maple Street", 101))

-- Display the entities
main :: IO ()
main = do
    print company
    print person
```

---

### 🧠 Explanation:

- **`type Entity a = (a, Address)`**:
  - This defines an alias where any type `a` (e.g. a name, or more detailed structure) is paired with an `Address`.
  - It doesn’t create a new data type, but makes your type signatures cleaner and more expressive.

