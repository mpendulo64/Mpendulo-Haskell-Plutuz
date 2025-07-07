HC1T1 - Task 1: Function Composition

```haskell
-- double: Multiplies a number by 2
double :: Int -> Int
double x = x * 2

-- increment: Increases a number by 1
increment :: Int -> Int
increment x = x + 1

-- doubleThenIncrement: Applies double first, then increment using function composition
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double

-- main: Runs the functions and prints results
main :: IO ()
main = do
    let value = 7
    putStrLn $ "Original value: " ++ show value
    putStrLn $ "Doubled: " ++ show (double value)
    putStrLn $ "Incremented: " ++ show (increment value)
    putStrLn $ "Double then increment: " ++ show (doubleThenIncrement value)
```

### How It Works:

* `doubleThenIncrement = increment . double` means it **first** doubles the value, **then** increments the result.
* For input `7`, it will compute `increment (double 7)` = `increment 14` = `15`.

### To Run It:

1. Save it in a file like `Main.hs`.
2. Run using:

   ```bash
   runghc Main.hs
   ```

### Expected Output:

```
Original value: 7
Doubled: 14
Incremented: 8
Double then increment: 15
```







