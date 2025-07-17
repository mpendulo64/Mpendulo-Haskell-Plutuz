HC15T2: Implement a basic self-driving AI car system that reacts to traffic light colors.
---



```haskell
-- Define the TrafficLight data type
data TrafficLight = Red | Yellow | Green deriving (Show, Eq)

-- AI car decision function based on traffic light color
reactToTrafficLight :: TrafficLight -> String
reactToTrafficLight Red    = "Stop the car."
reactToTrafficLight Yellow = "Prepare to stop."
reactToTrafficLight Green  = "Go ahead."

-- Simulate receiving traffic light input and react
main :: IO ()
main = do
    putStrLn "Enter traffic light color (Red, Yellow, Green):"
    input <- getLine
    case parseTrafficLight input of
        Just light -> putStrLn $ "AI Car action: " ++ reactToTrafficLight light
        Nothing    -> putStrLn "Invalid traffic light color entered."

-- Parse user input into TrafficLight type
parseTrafficLight :: String -> Maybe TrafficLight
parseTrafficLight s =
    case map toLower s of
        "red"    -> Just Red
        "yellow" -> Just Yellow
        "green"  -> Just Green
        _        -> Nothing

-- Helper function to convert string to lowercase
toLower :: Char -> Char
toLower c
    | 'A' <= c && c <= 'Z' = toEnum (fromEnum c + 32)
    | otherwise            = c
```

---

## 📘 Explanation

* `TrafficLight` data type models the possible light states.
* `reactToTrafficLight` decides the car's action for each color.
* `main` reads user input, parses it, and outputs the action.
* `parseTrafficLight` converts the input string (case-insensitive) to `TrafficLight`.
* If input is invalid, the program informs the user.

---


