HC15T9: Use the try function to catch file IO exceptions and handle them gracefully.
---



```haskell
import System.IO
import Control.Exception
import Data.Typeable

main :: IO ()
main = do
    putStrLn "Enter the name of the file to read:"
    fileName <- getLine

    result <- try (readFile fileName) :: IO (Either IOException String)

    case result of
        Left err -> putStrLn $ "Could not open file: " ++ show err
        Right content -> do
            putStrLn "File content:"
            putStrLn content
```

---

## 📘 Explanation

### ✅ `try` Function

```haskell
try :: Exception e => IO a -> IO (Either e a)
```

* Wraps an `IO` action (like `readFile`)
* Returns `Right result` on success
* Returns `Left exception` on failure
* Lets you **handle errors in pure Haskell** without crashing

---

### ✅ Type Annotation

We use:

```haskell
try (readFile fileName) :: IO (Either IOException String)
```

This tells the compiler we're catching **I/O-related exceptions**, like:

* File not found
* Permission denied
* Encoding issues

---

### ✅ Behavior

#### Example 1: File exists

```
Enter the name of the file to read:
example.txt
File content:
Hello, world!
```

#### Example 2: File does not exist

```
Enter the name of the file to read:
nofile.txt
Could not open file: nofile.txt: openFile: does not exist (No such file or directory)
```

---

## ✅ Why use `try`?

* More **granular** and **recoverable** than `catch`
* Works well when you want to **pattern match** on `Either`
* Great for programs that shouldn't crash on I/O errors

---

