HC2T7 - Task 7: Boolean Expressions

```haskell
-- Boolean expressions in Haskell

main :: IO ()
main = do
    putStrLn "True using &&:"
    print (True && True)         -- Evaluates to True

    putStrLn "\nFalse using ||:"
    print (False || False)       -- Evaluates to False

    putStrLn "\nTrue using not:"
    print (not False)            -- Evaluates to True

    putStrLn "\nA comparison that returns False:"
    print (10 < 5)               -- Evaluates to False
```

### ✅ Explanation:

- `True && True`: both conditions are true → result is `True`
- `False || False`: neither condition is true → result is `False`
- `not False`: flips `False` to `True`
- `10 < 5`: a comparison that is clearly false















