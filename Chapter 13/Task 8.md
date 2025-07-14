HC13T8
Demonstrate how to handle name conflicts between two imported modules, using qualified imports.


---


```haskell
import qualified Data.Map as M
import qualified Data.List as L

main :: IO ()
main = do
    -- Using Data.List's filter to work on a list
    let names = ["Alice", "Bob", "Charlie"]
    let shortNames = L.filter (\n -> length n <= 4) names
    putStrLn $ "👥 Short names: " ++ show shortNames

    -- Using Data.Map's filter to work on a map
    let scores = M.fromList [("Alice", 85), ("Bob", 92), ("Charlie", 68)]
    let highScores = M.filter (> 80) scores
    putStrLn $ "🎯 High scores: " ++ show highScores
```

---

### 🧠 Explanation

- **`qualified` import**: You prefix functions with the alias (`M.` or `L.`) to specify their origin.
- **`Data.List.filter` vs `Data.Map.filter`**: Avoids ambiguity by keeping each module’s functions accessible via its alias.
- **Aliasing (`as`)**: Makes code cleaner and avoids long module names.

---

