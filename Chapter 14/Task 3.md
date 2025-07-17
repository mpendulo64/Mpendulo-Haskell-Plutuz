HC14T3: Enable the NumericUnderscores extension. Create variables with large numbers and print them.


---


```haskell
{-# LANGUAGE NumericUnderscores #-}

module Main where

main :: IO ()
main = do
    let population = 1_000_000       -- 1 million
    let budget     = 25_000_000.50   -- 25 million and 50 cents (Float/Double)
    let distance   = 149_600_000     -- Distance from Earth to Sun in km

    putStrLn $ "Population: " ++ show population
    putStrLn $ "Budget: " ++ show budget
    putStrLn $ "Distance to Sun: " ++ show distance ++ " km"
```

---

## 📘 **Explanation**

### ✅ `{-# LANGUAGE NumericUnderscores #-}`

* This **enables the `NumericUnderscores` extension**, which allows you to add underscores (`_`) inside numeric literals for readability.
* Available since **GHC 8.6+**.

---

