HC3T3 - Task 3: Convert an RGB color to a hex string using let bindings

```haskell
import Text.Printf (printf)

-- Function to convert RGB values to hexadecimal string
rgbToHex :: (Int, Int, Int) -> String
rgbToHex (r, g, b) =
    let red   = printf "%02X" r
        green = printf "%02X" g
        blue  = printf "%02X" b
    in red ++ green ++ blue

-- Testing the function
main :: IO ()
main = do
    putStrLn $ "RGB (255, 0, 127) -> Hex: #" ++ rgbToHex (255, 0, 127)
    putStrLn $ "RGB (0, 255, 64) -> Hex: #" ++ rgbToHex (0, 255, 64)
```

### 🔍 Explanation:

- **`printf "%02X"`**:
  - Formats an integer as a **2-digit uppercase hexadecimal** value.
  - Adds a leading `0` if the value is less than 16 (e.g., `0x0A` becomes `"0A"`).
- **`let ... in`**:
  - Binds the formatted red, green, and blue values to variables inside the function.
- **Concatenation**:
  - We join `red`, `green`, and `blue` strings into one hex code like `"FF007F"`.

### ✅ Output when run:

```
RGB (255, 0, 127) -> Hex: #FF007F
RGB (0, 255, 64) -> Hex: #00FF40
```


