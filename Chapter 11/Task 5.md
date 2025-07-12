-- HC11T5: Write a program that repeatedly asks the user for input until they enter "quit".


---



```haskell
-- Program that loops until user enters "quit"
main :: IO ()
main = loop

loop :: IO ()
loop = do
    putStrLn "💬 Type something (or \"quit\" to exit):"
    input <- getLine
    if input == "quit"
        then putStrLn "👋 Goodbye!"
        else do
            putStrLn $ "📣 You typed: " ++ input
            loop  -- repeat until "quit" is entered
```

---

### 🧠 Explanation

- **`main :: IO ()`**  
  Starts the program by invoking `loop`.

- **`loop :: IO ()`**  
  A recursive function that:
  - Prompts the user.
  - Reads their input with `getLine`.
  - Checks whether the input is `"quit"`.
    - If yes: prints a farewell and exits.
    - If not: echoes the input and calls itself again.

- **Recursion in IO**  
  Instead of using `while` or loops (which Haskell doesn't have), recursion is used to repeat actions in the `IO` monad.

---

