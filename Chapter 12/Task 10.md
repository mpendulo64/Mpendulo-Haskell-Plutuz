HC12T10
Create a Haskell program that defines a module for mathematical operations and demonstrates its use in the main function.


---

### 📦 Step 1: Define the Module (in a separate file named `MathOps.hs`)

```haskell
module MathOps (
    add,
    subtract',
    multiply,
    divide
) where

-- Addition
add :: Int -> Int -> Int
add x y = x + y

-- Subtraction
subtract' :: Int -> Int -> Int
subtract' x y = x - y

-- Multiplication
multiply :: Int -> Int -> Int
multiply x y = x * y

-- Division with error handling for zero
divide :: Int -> Int -> Maybe Float
divide _ 0 = Nothing
divide x y = Just (fromIntegral x / fromIntegral y)
```

> Note: The apostrophe in `subtract'` avoids name clash with `Prelude.subtract`.

---

### 🚀 Step 2: Use the Module in `Main.hs`

```haskell
import MathOps

-- Main program demonstrating the math module
main :: IO ()
main = do
    let a = 10
    let b = 5

    putStrLn $ "➕ " ++ show a ++ " + " ++ show b ++ " = " ++ show (add a b)
    putStrLn $ "➖ " ++ show a ++ " - " ++ show b ++ " = " ++ show (subtract' a b)
    putStrLn $ "✖️ " ++ show a ++ " * " ++ show b ++ " = " ++ show (multiply a b)

    case divide a b of
        Just result -> putStrLn $ "➗ " ++ show a ++ " / " ++ show b ++ " = " ++ show result
        Nothing     -> putStrLn "🚫 Division by zero!"
```

---

### 🧠 Explanation

- **Modular Design**:
  - Keeps math functions organized in `MathOps`.
  - Promotes reuse and cleaner separation of logic.

- **`Maybe` type in `divide`**:
  - Safe handling for division by zero.
  - Produces `Nothing` if `y` is `0`, otherwise returns `Just result`.

- **Importing the Module**:
  - `import MathOps` pulls in all exported functions.
  - You can compile both files together, or use GHCi to load them interactively.

---

