HC14T6: Create a cabal project structure with src and app directories. Place the main module in the app folder and additional modules in src.

```
my-project/
├── app/
│   └── Main.hs        -- Main executable
├── src/
│   └── Utils.hs       -- Custom module
├── my-project.cabal   -- Cabal configuration
└── other files...
```

We'll:

* Initialize the project with `cabal init`
* Place `Main.hs` in `app/`
* Create an extra module `Utils.hs` in `src/`
* Configure `.cabal` file to recognize both `app` and `src`

---

## ✅ Step-by-Step Instructions

### 1. 📁 **Create project folder**

```bash
mkdir my-project
cd my-project
```

---

### 2. 🚀 **Initialize with Cabal**

```bash
cabal init
```

Use the following answers:

* Package name: `my-project`
* Package type: **Executable**
* Main module: `Main.hs`
* Source directory: `app`
* Build tool: `cabal`

---

### 3. 📄 **Create `app/Main.hs`**

```haskell
-- app/Main.hs
module Main where

import Utils (greet)

main :: IO ()
main = do
    putStrLn "Starting program..."
    putStrLn $ greet "Haskell"
```

---

### 4. 📄 **Create `src/Utils.hs`**

```haskell
-- src/Utils.hs
module Utils (greet) where

greet :: String -> String
greet name = "Hello, " ++ name ++ "!"
```

---

### 5. 🛠 **Edit `my-project.cabal`**

Locate the `executable` section and update it to use both `app/` and `src/` directories:

```cabal
executable my-project
  main-is:             Main.hs
  hs-source-dirs:      app, src
  build-depends:       base >=4.7 && <5
  default-language:    Haskell2010
```

---

### 6. 🧪 **Build & Run**

```bash
cabal build
cabal run
```


---

## 📘 Explanation

* **`hs-source-dirs: app, src`**: Tells Cabal where to look for modules (`Main.hs` in `app`, `Utils.hs` in `src`)
* **`module Utils (greet)`**: Explicitly exports the `greet` function
* `Main` imports `Utils`, calls `greet`, and prints a result

---

