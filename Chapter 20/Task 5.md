HC20T5: Reader Monad for Configurable Greeting
Use the Reader monad to create a configuration-based system for greeting users.
---

### **Working Haskell Code**

```haskell
module Main where

import Control.Monad.Reader

-- | Configuration data type
data Config = Config
  { greeting :: String   -- Greeting phrase
  , punctuation :: String -- Punctuation to end the message
  }

-- | Our Reader monad type alias for convenience
type App a = Reader Config a

-- | Function that greets a given user using the configuration
greetUser :: String -> App String
greetUser name = do
    cfg <- ask  -- Get the current configuration
    return $ greeting cfg ++ ", " ++ name ++ punctuation cfg

-- | Function that greets a list of users
greetUsers :: [String] -> App [String]
greetUsers names = mapM greetUser names

main :: IO ()
main = do
    -- Example configuration
    let config = Config { greeting = "Hello", punctuation = "!" }

    -- Run the Reader monad with the given configuration
    let messages = runReader (greetUsers ["Alice", "Bob", "Charlie"]) config

    -- Print results
    putStrLn "---- Greetings ----"
    mapM_ putStrLn messages
```

---

### ✅ **Explanation**

1. **Configuration Type**

   ```haskell
   data Config = Config
     { greeting :: String
     , punctuation :: String
     }
   ```

   * Holds our app's configuration (greeting phrase + punctuation).
   * Can be extended easily (e.g., add language, theme, etc.).

2. **Reader Monad**

   * `Reader Config a` represents a computation that can **read from a shared `Config`**.
   * We define `type App a = Reader Config a` for readability.

3. **Accessing Configuration**

   * `ask :: Reader Config Config` retrieves the current configuration.
   * We use it in `greetUser` to construct a message dynamically.

4. **Running the Reader**

   * `runReader (greetUsers [...]) config` applies the configuration to our computation.

5. **Output**
   If we run the code, we get:

   ```
   ---- Greetings ----
   Hello, Alice!
   Hello, Bob!
   Hello, Charlie!
   ```

---

### 💡 Why Reader Monad?

* It removes the need to **pass `config` manually** to every function.
* Functions stay pure and easy to compose.
* If we wanted to change the greeting style (e.g., `"Welcome"` instead of `"Hello"`), we just change the `Config` and rerun.

---

