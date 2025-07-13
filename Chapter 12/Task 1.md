HC12T1
Create a Haskell program that prints "Welcome to Haskell Programming!" to the terminal.


---


```haskell
-- Welcome program in Haskell
main :: IO ()
main = putStrLn "Welcome to Haskell Programming!"
```

---

### 🧠 Explanation

- **`main :: IO ()`**  
  Declares the `main` entry point — every Haskell program that does input/output starts here.

- **`putStrLn`**  
  Is the standard function for printing a string followed by a newline to the terminal.

- **String Literal**  
  `"Welcome to Haskell Programming!"` is directly passed to `putStrLn` to display.

---

