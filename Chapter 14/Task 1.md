HC14T1: Create a Haskell project using cabal init. Add a main executable that outputs "Hello, Cabal!".
---


## ✅ Step-by-Step Instructions

### 1. **Create a new project directory**

```bash
mkdir hello-cabal
cd hello-cabal
```

---

### 2. **Initialize the project using `cabal init`**

```bash
cabal init
```

* Answer the interactive prompts like this:

  * **Package name:** `hello-cabal`
  * **Package type:** `Executable`
  * **Main module:** `Main.hs`
  * **Build tool:** `cabal`
  * Accept other defaults or customize as you like.

This generates a `hello-cabal.cabal` file and a `Main.hs` stub.

---

### 3. **Edit `Main.hs`**

In the `app/` folder (if generated), or root, add the following:

```haskell
-- app/Main.hs
module Main where

main :: IO ()
main = putStrLn "Hello, Cabal!"
```

If `Main.hs` is at the root (depends on your options during `cabal init`), make sure it looks like the above.

---

### 4. **Edit `hello-cabal.cabal` (if needed)**

Make sure the `.cabal` file has an `executable` section like this:

```cabal
executable hello-cabal
  main-is:             Main.hs
  hs-source-dirs:      app
  build-depends:       base >=4.7 && <5
  default-language:    Haskell2010
```

> Adjust `hs-source-dirs` depending on where your `Main.hs` is (`app/` or `src/` or root).

---

### 5. **Build and run the project**

```bash
cabal build
cabal run hello-cabal
```

---

### ✅ Output:

```
Hello, Cabal!
```

---

