HC2T1 - Task 1: Checking Types in GHCi


---

### ✅ **How to Check Types in GHCi**

1. Open your terminal or command prompt.
2. Start GHCi by typing:

```bash
ghci
```

3. Then enter the following expressions **one at a time** in GHCi:

```haskell
:type 42
:type 3.14
:type "Haskell"
:type 'Z'
:type True && False
```

---

### 💡 Expected Output:

```haskell
Prelude> :type 42
42 :: Num a => a

Prelude> :type 3.14
3.14 :: Fractional a => a

Prelude> :type "Haskell"
"Haskell" :: [Char]

Prelude> :type 'Z'
'Z' :: Char

Prelude> :type True && False
True && False :: Bool
```

---

### 📝 If you want a `.hs` file that evaluates the expressions (not types):

```haskell
main :: IO ()
main = do
    print (42 :: Int)
    print (3.14 :: Double)
    print ("Haskell" :: String)
    print ('Z' :: Char)
    print (True && False)
```





