HC11T2: Implement the fancyFunction for the WeAccept type class and test it with various types like Cardano, Cash, and Country.

---



```haskell
-- Define some simple types
data Cardano = Cardano deriving Show
data Cash    = Cash deriving Show
data Country = Country String deriving Show

-- Define the WeAccept type class
class WeAccept a where
    isAccepted   :: a -> Bool
    fancyFunction :: a -> String

-- Implement WeAccept for Cardano
instance WeAccept Cardano where
    isAccepted _ = True
    fancyFunction _ = "🚀 Cardano accepted and ready for staking!"

-- Implement WeAccept for Cash
instance WeAccept Cash where
    isAccepted _ = True
    fancyFunction _ = "💵 Good ol’ cash is always welcome."

-- Implement WeAccept for Country
instance WeAccept Country where
    isAccepted (Country name) = name == "South Africa"
    fancyFunction (Country name)
        | isAccepted (Country name) = "🌍 Welcome, " ++ name ++ "! You're on the VIP list."
        | otherwise                 = "❌ Sorry, " ++ name ++ " is not currently supported."

-- Example usage
main :: IO ()
main = do
    print $ fancyFunction Cardano
    print $ fancyFunction Cash
    print $ fancyFunction (Country "South Africa")
    print $ fancyFunction (Country "Atlantis")
```

---

### 🧠 Explanation

- **Types**:  
  - `Cardano`, `Cash`, and `Country` are simple types we use for demonstration.
  - `Country` wraps a `String`, letting us customize by country name.

- **Type Class `WeAccept`**:  
  - Includes `isAccepted` to check acceptance.
  - Adds `fancyFunction :: a -> String` to provide an expressive message.

- **Instances**:  
  - `Cardano` and `Cash` are always accepted.
  - `Country` only accepts `"South Africa"` and returns a distinct message accordingly.

- **Output**:
  ```
  "🚀 Cardano accepted and ready for staking!"
  "💵 Good ol’ cash is always welcome."
  "🌍 Welcome, South Africa! You're on the VIP list."
  "❌ Sorry, Atlantis is not currently supported."
  ```

---

