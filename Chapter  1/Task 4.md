HC1T4 - Task 4: Composing a Function to Process Player Data

* `extractPlayers`: Extracts player names from a list of `(String, Int)` tuples.
* `sortByScore`: Sorts the list of players by score in descending order.
* `topThree`: Gets the top 3 players.
* `getTopThreePlayers`: Composes the above functions to return the names of the top 3 players.

```haskell
import Data.List (sortBy)
import Data.Ord (comparing)

-- Extract player names
extractPlayers :: [(String, Int)] -> [String]
extractPlayers = map fst

-- Sort by score in descending order
sortByScore :: [(String, Int)] -> [(String, Int)]
sortByScore = sortBy (flip (comparing snd))

-- Take top three players
topThree :: [(String, Int)] -> [(String, Int)]
topThree = take 3

-- Compose all functions
getTopThreePlayers :: [(String, Int)] -> [String]
getTopThreePlayers = extractPlayers . topThree . sortByScore

-- Sample data and main function
main :: IO ()
main = do
    let players = [("Alice", 90), ("Bob", 85), ("Charlie", 92), ("Dave", 88), ("Eve", 80)]
    let topPlayers = getTopThreePlayers players
    putStrLn "Top 3 Players:"
    mapM_ putStrLn topPlayers
```

### ✅ Output when you run it:

```
Top 3 Players:
Charlie
Alice
Dave
```




