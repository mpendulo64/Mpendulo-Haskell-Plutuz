HC8T5: Define a type Person using a record syntax that includes name :: String, age :: Int, and isEmployed :: Bool. Create a person1 who is employed, and a person2 who is unemployed.

```haskell
-- Define the Person type using record syntax
data Person = Person
    { name       :: String
    , age        :: Int
    , isEmployed :: Bool
    } deriving Show

-- Create person1 who is employed
person1 :: Person
person1 = Person
    { name = "Alice"
    , age = 30
    , isEmployed = True
    }

-- Create person2 who is unemployed
person2 :: Person
person2 = Person
    { name = "Bob"
    , age = 24
    , isEmployed = False
    }

-- Example usage
main :: IO ()
main = do
    print person1
    print person2
```

### 🧠 Explanation:

- **Record syntax** lets us name each field (`name`, `age`, `isEmployed`), making both data construction and access clearer and safer.
- **`deriving Show`** allows instances of `Person` to be printed in the console.
- You can access specific fields like:  
  ```haskell
  name person1        -- "Alice"
  age person2         -- 24
  isEmployed person2  -- False
  ```

 
