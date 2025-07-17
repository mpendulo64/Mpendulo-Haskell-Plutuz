HC14T7: Modify the .cabal file to support a library component alongside the main executable.

* ✅ A **library component** (with modules in `src/`)
* ✅ A **main executable** (with `Main.hs` in `app/`) that uses the library

This is a **common and recommended structure** for Haskell projects.

---

## ✅ Project Structure

```
my-project/
├── app/
│   └── Main.hs           -- Main executable
├── src/
│   └── Utils.hs          -- Library module
├── my-project.cabal      -- Cabal config
```

---

## ✅ 1. Modified `.cabal` File

Below is the key part of your updated `my-project.cabal`:

```cabal
cabal-version:       >=1.10
name:                my-project
version:             0.1.0.0
build-type:          Simple

-- Define the library component
library
  exposed-modules:     Utils
  hs-source-dirs:      src
  build-depends:       base >=4.7 && <5
  default-language:    Haskell2010

-- Define the executable that depends on the library
executable my-project
  main-is:             Main.hs
  hs-source-dirs:      app
  build-depends:       base >=4.7 && <5,
                       my-project       -- Depends on the local library
  default-language:    Haskell2010
```

---

## ✅ 2. `src/Utils.hs` (Library Module)

```haskell
-- src/Utils.hs
module Utils (greet) where

greet :: String -> String
greet name = "Hello, " ++ name ++ "!"
```

---

## ✅ 3. `app/Main.hs` (Main Executable)

```haskell
-- app/Main.hs
module Main where

import Utils (greet)

main :: IO ()
main = do
    putStrLn "Running main executable..."
    putStrLn $ greet "Cabal"
```

---

## ✅ 4. Build and Run

```bash
cabal build
cabal run my-project
```

---



---

## 📘 Explanation

### ✅ Why Split into Library + Executable?

* Encourages **modular design**
* Shared code lives in the **library** (`src/`)
* `Main.hs` in `app/` depends on and **reuses** library code

### ✅ Key Cabal Fields

| Section          | Purpose                                                 |
| ---------------- | ------------------------------------------------------- |
| `library`        | Declares reusable modules (e.g. `Utils`)                |
| `executable`     | Declares the main app, uses `build-depends: my-project` |
| `hs-source-dirs` | Points to code location (`src`, `app`)                  |

---


