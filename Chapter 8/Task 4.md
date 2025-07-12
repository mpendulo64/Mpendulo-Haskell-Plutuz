HC8T4: Define a new type Employee using record syntax with fields name :: String and experienceInYears :: Float. Create an employee richard with 7.5 years of experience
```haskell
-- Define Employee type using record syntax
data Employee = Employee
    { name :: String
    , experienceInYears :: Float
    } deriving Show

-- Create an employee named Richard with 7.5 years of experience
richard :: Employee
richard = Employee
    { name = "Richard"
    , experienceInYears = 7.5
    }

-- Example usage
main :: IO ()
main = print richard
```

### 🧠 Explanation:

- **`data Employee = Employee { ... }`** uses **record syntax** to define fields with names (`name` and `experienceInYears`). This allows easy access to individual fields later.
- **`deriving Show`** lets you print `Employee` values conveniently.
- **Instance `richard`** is constructed using labeled field assignment for clarity and correctness.



