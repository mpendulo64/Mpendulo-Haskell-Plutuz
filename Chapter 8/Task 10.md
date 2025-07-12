HC8T10: Using deriving Show, define a type Book with fields title :: String, author :: String, and year :: Int. Create a Book instance for a book and print it using the Show instance
```haskell
-- Define the Book type using record syntax
data Book = Book
    { title  :: String
    , author :: String
    , year   :: Int
    } deriving Show

-- Create an instance of Book
myBook :: Book
myBook = Book
    { title  = "Learn You a Haskell for Great Good!"
    , author = "Miran Lipovača"
    , year   = 2011
    }

-- Example usage
main :: IO ()
main = print myBook
```

---

### 🧠 Explanation:

- **Record Syntax**:  
  This allows you to define named fields (`title`, `author`, `year`) which makes the code both readable and easily accessible.
  
- **`deriving Show`**:  
  Automatically gives the `Book` type the ability to be printed. No need to manually write a `Show` instance.

- **Instance `myBook`**:  
  Uses labeled field assignments to construct the book clearly.

- **`print myBook`**:  
  Outputs the full record as a string using the default formatting provided by `Show`.

---

