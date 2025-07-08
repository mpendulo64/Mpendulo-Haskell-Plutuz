HC2T3 - Task 3: Immutable Variables

```haskell
-- More immutable variable definitions in Haskell
language :: String
language = "Haskell"

year :: Int
year = 2025

temperature :: Float
temperature = 23.7

isRaining :: Bool
isRaining = False

main :: IO ()
main = do
    putStrLn $ "Language: " ++ language
    putStrLn $ "Year: " ++ show year
    putStrLn $ "Current temperature: " ++ show temperature ++ "°C"
    putStrLn $ "Is it raining? " ++ show isRaining

    -- Attempting to mutate 'year' (this will cause an error if uncommented)
    -- year = 2026  -- Not allowed in Haskell!
```




