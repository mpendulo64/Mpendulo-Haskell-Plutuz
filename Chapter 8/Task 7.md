HC8T7: Define a new type Animal using data with constructors Dog String and Cat String. Create a function describeAnimal :: Animal -> String that describes the animal. Create instances for a dog and a cat.

```haskell
-- Define Animal type with two constructors, each carrying a name
data Animal = Dog String | Cat String
    deriving Show

-- Function that describes the animal
describeAnimal :: Animal -> String
describeAnimal (Dog name) = "This is a dog named " ++ name ++ "."
describeAnimal (Cat name) = "This is a cat named " ++ name ++ "."

-- Create instances of Animal
dog1 :: Animal
dog1 = Dog "Rover"

cat1 :: Animal
cat1 = Cat "Whiskers"

-- Example usage
main :: IO ()
main = do
    putStrLn (describeAnimal dog1)   -- Output: This is a dog named Rover.
    putStrLn (describeAnimal cat1)   -- Output: This is a cat named Whiskers.
```

---

### 🧠 Explanation:

- **`data Animal = Dog String | Cat String`**: Declares an algebraic data type where both constructors carry a `String` value representing the animal’s name.
- **`describeAnimal`** uses **pattern matching** to distinguish between dogs and cats and constructs a sentence accordingly.
- `dog1` and `cat1` are instances using the constructors `Dog` and `Cat`, with their names embedded.

---

