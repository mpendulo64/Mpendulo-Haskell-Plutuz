HC2T4 - Task 4: Converting Between Infix and Prefix Notations

```haskell
-- Demonstrating infix to prefix and prefix to infix in Haskell
main :: IO ()
main = do
    -- Infix ➡️ Prefix
    putStrLn "Infix to Prefix:"
    print ((+) 5 3)         -- Equivalent to 5 + 3
    print ((*) 10 4)        -- Equivalent to 10 * 4
    print ((&&) True False) -- Equivalent to True && False

    -- Prefix ➡️ Infix
    putStrLn "\nPrefix to Infix:"
    print (7 + 2)           -- Equivalent to (+) 7 2
    print (6 * 5)           -- Equivalent to (*) 6 5
    print (True && False)   -- Equivalent to (&&) True False




