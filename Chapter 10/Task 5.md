HC10T5: Define a type class ShowDetailed with a function showDetailed :: a -> String and implement it for a type User.

---



```haskell
-- Define the User type using record syntax
data User = User
    { name  :: String
    , email :: String
    , age   :: Int
    } deriving Show

-- Define the ShowDetailed type class
class ShowDetailed a where
    showDetailed :: a -> String

-- Implement ShowDetailed for User
instance ShowDetailed User where
    showDetailed (User n e a) =
        "User Profile\n" ++
        "Name: " ++ n ++ "\n" ++
        "Email: " ++ e ++ "\n" ++
        "Age: " ++ show a

-- Example usage
main :: IO ()
main = do
    let user1 = User "Alice" "alice@example.com" 28
    putStrLn $ showDetailed user1
```

---

### 🧠 Explanation

- **`data User = User { ... }`**:  
  Defines a basic user profile with three fields using record syntax.

- **`class ShowDetailed a where ...`**:  
  Declares a new type class for formatting detailed string output.

- **Instance for `User`**:  
  Constructs a readable multi-line summary of a `User` value using string concatenation.

- **`main` usage**:  
  Creates one user and prints their profile using `showDetailed`.

---


