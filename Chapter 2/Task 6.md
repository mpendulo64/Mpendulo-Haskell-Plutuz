HC2T6 - Task 6: Understanding Int vs Integer

```haskell
-- Demonstrating bounded Int vs unbounded Integer

smallNumber :: Int
smallNumber = 2 ^ 62  -- This should work fine on most 64-bit systems

bigNumber :: Integer
bigNumber = 2 ^ 127   -- Integer can handle very large values

main :: IO ()
main = do
    putStrLn "Small number (2^62) as Int:"
    print smallNumber

    putStrLn "\nBig number (2^127) as Integer:"
    print bigNumber

    putStrLn "\nAttempting to evaluate 2^64 :: Int"
    let overflowed = (2 ^ 64) :: Int
    print overflowed  -- Likely to overflow and show a negative or unexpected value!
```

### 🧠 Notes:

- `Int` is fixed-size and platform dependent. On 64-bit systems, its max is typically `2^63 - 1`, so `2^62` works but `2^64` may overflow.
- `Integer` is arbitrary-precision—it’ll happily swallow `2^127` and grin.

























































