HC15T4: Use a handler function to catch and handle traffic light exceptions.

---


```haskell
{-# LANGUAGE DeriveDataTypeable #-}

import Control.Exception
import Data.Typeable

-- Step 1: Define a custom exception type
data TrafficLightException = InvalidTrafficLight String
    deriving (Show, Typeable)

instance Exception TrafficLightException

-- Step 2: Function that may throw a traffic light error
parseTrafficLight :: String -> IO String
parseTrafficLight input =
    case map toLower input of
        "red"    -> return "Stop"
        "yellow" -> return "Prepare to stop"
        "green"  -> return "Go"
        other    -> throwIO (InvalidTrafficLight ("Invalid color: " ++ other))

-- Step 3: Handler function for the custom exception
handleTrafficLightError :: TrafficLightException -> IO String
handleTrafficLightError (InvalidTrafficLight msg) = return $ "Error: " ++ msg

-- Helper function: convert character to lowercase
toLower :: Char -> Char
toLower c
    | 'A' <= c && c <= 'Z' = toEnum (fromEnum c + 32)
    | otherwise            = c

-- Step 4: Main function with exception handling using 'catch'
main :: IO ()
main = do
    putStrLn "Enter traffic light color:"
    input <- getLine
    action <- parseTrafficLight input `catch` handleTrafficLightError
    putStrLn $ "Car action: " ++ action
```

---

## 📘 Explanation

### ✅ `data TrafficLightException`

* A custom exception that wraps an error message.
* Must derive `Typeable` and `Show` and implement the `Exception` type class.

---

### ✅ `parseTrafficLight`

* Attempts to interpret a user string as a traffic light command.
* If input is invalid, it throws a `TrafficLightException`.

---

### ✅ `handleTrafficLightError`

* A function of type `TrafficLightException -> IO String`
* Used to **handle** the exception and return an alternative message.

---

### ✅ `catch` usage

* `parseTrafficLight input \`catch\` handleTrafficLightError\`
* If `parseTrafficLight` throws an exception, `handleTrafficLightError` is run.

---


