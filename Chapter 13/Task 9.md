HC13T9
Create a function that demonstrates renaming a module namespace and uses functions from both renamed modules.


---


```haskell
-- Qualified imports with custom namespace aliases
import qualified Data.Map as M
import qualified Data.Set as S

-- Demonstration function that uses both Map and Set
main :: IO ()
main = do
    -- Using Data.Map with alias M
    let phoneBook = M.fromList [("Alice", "123"), ("Bob", "456")]
    putStrLn $ "📞 Bob's number: " ++ show (M.lookup "Bob" phoneBook)

    -- Using Data.Set with alias S
    let names = S.fromList ["Alice", "Bob", "Charlie"]
    putStrLn $ "👥 Is 'Dave' in the set? " ++ show (S.member "Dave" names)
```

---

### 🧠 Explanation

- **`import qualified Data.Map as M`**  
  - You must prefix `Map` functions (like `fromList`, `lookup`) with `M.`  
  - This avoids conflict with other modules and improves clarity.

- **`import qualified Data.Set as S`**  
  - Likewise, `Set` functions (like `fromList`, `member`) must be prefixed with `S.`

- **`M.lookup "Bob" phoneBook`**  
  - Searches for "Bob" in the `Map`.

- **`S.member "Dave" names`**  
  - Checks for membership in the `Set`.

---

