HC15T1: Handle exceptions in a program that reads a file and calculates velocity based on user input.

* Reads a file containing distance (a number)
* Asks the user to input time
* Calculates velocity = distance / time
* Handles exceptions gracefully:

  * File not found
  * Invalid number parsing
  * Division by zero
  * Other IO errors

---


```haskell
import Control.Exception (catch, IOException)
import System.IO.Error (isDoesNotExistError)
import Text.Read (readMaybe)

main :: IO ()
main = do
    -- Handle file reading exceptions
    distanceResult <- readDistanceFromFile "distance.txt"
    case distanceResult of
        Left errMsg -> putStrLn $ "Error reading distance: " ++ errMsg
        Right distance -> do
            putStrLn $ "Distance read from file: " ++ show distance
            putStrLn "Enter time taken (in seconds):"
            timeInput <- getLine
            case readMaybe timeInput :: Maybe Double of
                Nothing -> putStrLn "Invalid input for time. Please enter a valid number."
                Just time
                    | time == 0 -> putStrLn "Time cannot be zero (division by zero)."
                    | time < 0  -> putStrLn "Time cannot be negative."
                    | otherwise -> do
                        let velocity = distance / time
                        putStrLn $ "Calculated velocity: " ++ show velocity ++ " units per second."

-- Function to read distance from a file with exception handling
readDistanceFromFile :: FilePath -> IO (Either String Double)
readDistanceFromFile path = 
    catch
        (do
            content <- readFile path
            case readMaybe content :: Maybe Double of
                Just d  -> return $ Right d
                Nothing -> return $ Left "File content is not a valid number."
        )
        handleReadError

-- Exception handler for file read errors
handleReadError :: IOException -> IO (Either String Double)
handleReadError e
    | isDoesNotExistError e = return $ Left "File does not exist."
    | otherwise             = return $ Left $ "IO error: " ++ show e
```

---

## 📘 Explanation

* `readDistanceFromFile` reads the file and attempts to parse its contents as a `Double`.
* Uses `catch` to handle IO exceptions like file not found.
* If file content is invalid (not a number), returns an error message.
* The main program asks the user for time, parses it safely using `readMaybe`.
* Checks for zero or negative time to avoid division errors.
* Prints calculated velocity if all inputs are valid.

---


