-- HC11T7: Write a program that prints a list of options to the user and executes different code based on the user's choice.


---


```haskell
-- Interactive menu-driven Haskell program
main :: IO ()
main = do
    putStrLn "🎯 Choose an option:"
    putStrLn "1. Greet"
    putStrLn "2. Add two numbers"
    putStrLn "3. Convert a string to uppercase"
    putStrLn "4. Quit"
    menuLoop

menuLoop :: IO ()
menuLoop = do
    putStr "👉 Enter your choice (1-4): "
    choice <- getLine
    case choice of
        "1" -> do
            putStrLn "👋 Hello there!"
            menuLoop

        "2" -> do
            putStrLn "➕ Enter first number:"
            x <- getLine
            putStrLn "➕ Enter second number:"
            y <- getLine
            let sum = read x + read y :: Int
            putStrLn $ "🧮 The sum is: " ++ show sum
            menuLoop

        "3" -> do
            putStrLn "🔠 Enter a string:"
            str <- getLine
            putStrLn $ "📢 Uppercase: " ++ map toUpper str
            menuLoop

        "4" -> putStrLn "👋 Exiting... Goodbye!"

        _ -> do
            putStrLn "❌ Invalid choice. Please try again."
            menuLoop

-- Required import for toUpper
import Data.Char (toUpper)
```

---

### 🧠 Explanation

- **Main Menu**:
  - Prints a list of options using `putStrLn`.
  - Calls `menuLoop` to process user input.

- **menuLoop**:
  - Reads the user’s input.
  - Uses `case` for clean branching logic.
  - Repeats unless the user chooses `"4"` to quit.

- **Branching Actions**:
  - `"1"`: Prints a greeting.
  - `"2"`: Reads two numbers, adds them, prints result.
  - `"3"`: Converts a string to uppercase using `map toUpper`.
  - `"4"`: Exits.
  - Any other input: Re-prompts user.

---

