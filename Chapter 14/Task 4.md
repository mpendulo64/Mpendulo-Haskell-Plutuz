HC14T4: Enable the TypeApplications extension and create a function that reads a String and converts it to an Int using read.


---



```haskell
{-# LANGUAGE TypeApplications #-}

module Main where

-- Function that reads a String and converts it to an Int using type application
stringToInt :: String -> Int
stringToInt str = read @Int str

-- Main function to test stringToInt
main :: IO ()
main = do
    let input = "12345"
    let result = stringToInt input
    putStrLn $ "Converted string \"" ++ input ++ "\" to Int: " ++ show result
```

---

## 📘 **Explanation**

### ✅ `{-# LANGUAGE TypeApplications #-}`

* Enables the ability to **specify types explicitly** using the `@` symbol.
* Useful when the compiler can't infer the type for polymorphic functions like `read`, `show`, or `id`.

---

### ✅ `read @Int str`

* `read` has the type: `read :: Read a => String -> a`
* By default, `read` needs type inference or annotation.
* Using `@Int` tells the compiler: “treat this `read` as producing an `Int`”.

---


---

### ✅ Build & Run Instructions

If using Cabal:

1. Ensure you have `Main.hs` in your source folder (e.g., `app/`).
2. Build and run:

```bash
cabal build
cabal run
```

---

