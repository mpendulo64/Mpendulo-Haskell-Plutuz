HC15T7: Implement a program that calculates velocity using optional values and handles parsing errors.

* ✅ **Calculates velocity**: `velocity = distance / time`
* ✅ Uses `Maybe` to represent **optional values**
* ✅ Uses `readMaybe` for **safe input parsing**
* ✅ Handles **invalid input and divide-by-zero errors** cleanly

---



```haskell
import Text.Read (readMaybe)

-- Safe division using Maybe to avoid division by zero
safeDiv :: (Eq a, Fractional a) => a -> a -> Maybe a
safeDiv _ 0 = Nothing
safeDiv x y = Just (x / y)

-- Safely parse a number from user input
parseInput :: String -> Maybe Double
parseInput = readMaybe

-- Calculate velocity from optional distance and time
calculateVelocity :: Maybe Double -> Maybe Double -> Maybe Double
calculateVelocity (Just d) (Just t) = safeDiv d t
calculateVelocity _ _               = Nothing

-- Main program
main :: IO ()
main = do
    putStrLn "Enter distance (in meters):"
    distInput <- getLine
    putStrLn "Enter time (in seconds):"
    timeInput <- getLine

    let maybeDist = parseInput distInput
        maybeTime = parseInput timeInput
        maybeVelocity = calculateVelocity maybeDist maybeTime

    case maybeVelocity of
        Just v  -> putStrLn $ "Velocity is " ++ show v ++ " m/s"
        Nothing -> putStrLn "Invalid input or division by zero. Cannot compute velocity."
```

---

## 📘 Explanation

### ✅ Components

| Function            | Purpose                                                               |
| ------------------- | --------------------------------------------------------------------- |
| `readMaybe`         | Parses a `String` into a `Maybe Double`, returning `Nothing` on error |
| `safeDiv`           | Divides two numbers, returning `Nothing` if divisor is zero           |
| `calculateVelocity` | Combines two `Maybe Double` values and safely computes velocity       |

---

### ✅ Error Handling Scenarios

* If the user enters **non-numeric input**: parsing fails (`Nothing`)
* If **time = 0**: `safeDiv` returns `Nothing`
* The final result is wrapped in a `Maybe`, and handled with a `case` expression

---

