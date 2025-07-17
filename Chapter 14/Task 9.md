HC14T9: Use language extension PartialTypeSignatures to allow wildcard types in a function signature.
---


```haskell
{-# LANGUAGE PartialTypeSignatures #-}

module Main where

-- Function with partial type signature
describeLength :: _ -> String
describeLength xs = "The length is: " ++ show (length xs)

main :: IO ()
main = do
    putStrLn $ describeLength [1, 2, 3]         -- list of Int
    putStrLn $ describeLength "Hello, world!"  -- String
```

---

## 📘 Explanation

### ✅ Language Extension

```haskell
{-# LANGUAGE PartialTypeSignatures #-}
```

* Enables support for using `_` as a **wildcard** in type signatures.
* You can write incomplete types and let the compiler **fill in the blanks**.

---

### ✅ Partial Type Example

```haskell
describeLength :: _ -> String
```

* The `_` tells the compiler:

  > “You figure out the input type based on how the function is used.”

* The full inferred type would be:

  ```haskell
  describeLength :: Foldable t => t a -> String
  ```

---

 

### 🛠 Note:

To **suppress GHC warnings** about the `_`, you can also compile with:

```bash
ghc -fno-warn-partial-type-signatures Main.hs
```

Or add this pragma at the top:

```haskell
{-# OPTIONS_GHC -fno-warn-partial-type-signatures #-}
```

---


