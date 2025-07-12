-- HC11T1: Write a program that asks the user for their name and prints a greeting.


1. Prompting for their name.
2. Reading their input.
3. Printing a personalized greeting.

---



```haskell
-- Interactive greeting program in Haskell
main :: IO ()
main = do
    putStrLn "👋 What's your name?"
    name <- getLine
    putStrLn $ "Hello, " ++ name ++ "! Welcome to the Haskellverse 🚀"
```

---

### 🧠 Explanation

- **`main :: IO ()`**  
  Declares the main entry point for an executable Haskell program. It performs input/output actions.

- **`putStrLn "..."`**  
  Prints a message to the console. The first `putStrLn` asks the user for their name.

- **`getLine`**  
  Reads a line of input from the user and binds it to the variable `name`.

- **`putStrLn $ "Hello, " ++ name ++ ...`**  
  Concatenates the greeting message and prints it.

---

