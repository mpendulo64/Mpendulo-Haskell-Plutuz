HC16T10: Define a function that counts the frequency of each character in a string.


---



```haskell
import qualified Data.Map as Map
import Data.Map (Map)

-- Function to count character frequencies
charFrequency :: String -> Map Char Int
charFrequency = foldr updateMap Map.empty
  where
    updateMap char freqMap = Map.insertWith (+) char 1 freqMap

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "📝 Enter a string:"
    input <- getLine
    let frequencies = charFrequency input
    putStrLn "📊 Character frequencies:"
    mapM_ print (Map.toList frequencies)
```

---

### 🧠 Explanation

- **`charFrequency :: String -> Map Char Int`**  
  The function takes a string and returns a `Map` with characters as keys and their counts as values.

- **`foldr updateMap Map.empty`**  
  Recursively processes each character in the string, updating the map.

- **`Map.insertWith (+) char 1 freqMap`**  
  If the character already exists in the map, it adds `1` to the existing count; otherwise, inserts `1`.

- **`Map.toList frequencies`**  
  Converts the `Map` into a list of `(Char, Int)` tuples for display.

---

