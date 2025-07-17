HC14T2: Modify the .cabal file to include a dependency on the random package and print a random number between 1 and 100.
---

## ✅ Step-by-Step Instructions

### 1. ✅ **Modify your `.cabal` file**

Open `hello-cabal.cabal` and **add `random` to the `build-depends`** section of your executable:

```cabal
executable hello-cabal
  main-is:             Main.hs
  hs-source-dirs:      app
  build-depends:       base >=4.7 && <5,
                       random >=1.2
  default-language:    Haskell2010
```

> If you don't have an `app/` folder, change `hs-source-dirs: .` or `src`, depending on where your `Main.hs` is.

---

### 2. ✅ **Update `Main.hs` to generate a random number**

```haskell
-- app/Main.hs
module Main where

import System.Random (randomRIO)

main :: IO ()
main = do
    number <- randomRIO (1, 100) :: IO Int
    putStrLn $ "Your random number between 1 and 100 is: " ++ show number
```

---

### 3. ✅ **Build and run the project**

```bash
cabal update           -- make sure package list is current
cabal build
cabal run hello-cabal
```

---

## 🧪 Example Output

```
Your random number between 1 and 100 is: 73
```

(Runs again → a new number will be printed each time.)

---

## 📘 Explanation

* **`randomRIO (1, 100)`** returns a random number between 1 and 100 (inclusive).
* It is an `IO Int`, so you must bind it with `<-` inside `do`.
* `random` is a standard library for random number generation.
* `build-depends` in `.cabal` tells Cabal what packages to include when compiling.

---



