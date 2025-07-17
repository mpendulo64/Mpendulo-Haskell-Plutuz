HC14T10: Write a cabal test suite for a module that verifies correct behavior of the counts function.
* A library module (`Utils.hs`) with the `counts` function
* A test suite using `HUnit`
* A properly configured `.cabal` file

---

## ✅ Project Structure

```
my-project/
├── app/
│   └── Main.hs            -- (optional executable)
├── src/
│   └── Utils.hs           -- Your library module
├── test/
│   └── CountsTest.hs      -- Test suite using HUnit
├── my-project.cabal       -- Cabal configuration
```

---

## ✅ 1. `src/Utils.hs` — The `counts` function

```haskell
module Utils (counts) where

import Data.List (group, sort)

-- Count character frequencies in a string
counts :: String -> [(Char, Int)]
counts str = map (\grp -> (head grp, length grp)) . group . sort $ str
```

---

## ✅ 2. `test/CountsTest.hs` — The test module

```haskell
module Main where

import Test.HUnit
import Utils (counts)

-- A simple test case
testCounts :: Test
testCounts = TestCase $
    assertEqual "counts 'hello'" 
        [('e',1),('h',1),('l',2),('o',1)] 
        (counts "hello")

-- Grouping all tests
tests :: Test
tests = TestList [TestLabel "Test counts function" testCounts]

main :: IO ()
main = do
    runTestTT tests
    return ()
```

---

## ✅ 3. Modify `my-project.cabal`

Add a **`library`** section (if not already present), and a **`test-suite`** section:

```cabal
-- Library
library
  hs-source-dirs:      src
  exposed-modules:     Utils
  build-depends:       base >=4.7 && <5
  default-language:    Haskell2010

-- Test suite
test-suite counts-tests
  type:                exitcode-stdio-1.0
  hs-source-dirs:      test
  main-is:             CountsTest.hs
  build-depends:       base >=4.7 && <5,
                       HUnit,
                       my-project        -- name of your package (i.e., the library)
  default-language:    Haskell2010
```

> 📝 Replace `my-project` in `build-depends` with your actual package name from the top of the `.cabal` file.

---

## ✅ 4. Add `HUnit` to your `.cabal` file's dependencies

You can also add `HUnit` to your `build-depends` globally (or just in the test suite as shown above).

If needed, install it via:

```bash
cabal install HUnit
```

---

## ✅ 5. Run the Test Suite

```bash
cabal test
```

---


---

## 📘 Explanation

* The `counts` function is placed in a shared library (`src/Utils.hs`)
* The test suite uses **`HUnit`** to define and run assertions
* The `.cabal` file defines the test suite with proper dependencies
* `exitcode-stdio-1.0` means test success/failure is determined by exit code and printed output

---


