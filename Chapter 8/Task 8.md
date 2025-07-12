HC8T8: Using type synonyms, create a type synonym Name for String and a type synonym Age for Int. Define a function greet :: Name -> Age -> String that takes a name and age and returns a greeting.

```haskell
-- Type synonyms for better readability
type Name = String
type Age  = Int

-- Function that returns a greeting using Name and Age
greet :: Name -> Age -> String
greet name age = "Hello, " ++ name ++ "! You are " ++ show age ++ " years old."
```

---

### 🧠 Explanation:

- **`type Name = String`** and **`type Age = Int`**:
  - These give meaningful aliases to basic types, making your function signatures more self-explanatory.
  - Internally, these are still `String` and `Int`, so no runtime overhead is introduced.

- **`greet :: Name -> Age -> String`**:
  - Takes a `Name` and an `Age`, returns a `String` greeting.
  - Uses `++` to concatenate strings.
  - `show age` converts the integer to a string so it can be included in the output.

---


