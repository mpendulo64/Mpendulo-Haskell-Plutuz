HC15T3: Define and throw a custom exception for traffic light errors.

---



```haskell
{-# LANGUAGE DeriveDataTypeable #-}

import Control.Exception
import Data.Typeable

-- Define a custom exception type for traffic light errors
data TrafficLightException = InvalidTrafficLight String
    deriving (Show, Typeable)

instance Exception TrafficLightException

-- Function to parse traffic light or throw an exception on error
parseTrafficLight :: String -> IO String
parseTrafficLight s =
    case map toLower s of
        "red"    -> return "Red"
        "yellow" -> return "Yellow"
        "green"  -> return "Green"
        other    -> throwIO (InvalidTrafficLight $ "Invalid traffic light color: " ++ other)

-- Helper function: convert character to lowercase
toLower :: Char -> Char
toLower c
    | 'A' <= c && c <= 'Z' = toEnum (fromEnum c + 32)
    | otherwise            = c

-- Main function demonstrating throwing and catching the exception
main :: IO ()
main = do
    putStrLn "Enter traffic light color:"
    input <- getLine
    result <- try (parseTrafficLight input) :: IO (Either TrafficLightException String)
    case result of
        Left ex  -> putStrLn $ "Caught exception: " ++ show ex
        Right color -> putStrLn $ "Valid traffic light color: " ++ color
```

---

## 📘 Explanation

* We define `TrafficLightException` deriving from `Show` and `Typeable`.
* Make it an instance of `Exception` so it can be thrown/caught.
* `parseTrafficLight` throws `InvalidTrafficLight` exception for invalid input using `throwIO`.
* In `main`, we use `try` to catch the exception and handle it gracefully.
* The program prints the exception message if input is invalid.

---

