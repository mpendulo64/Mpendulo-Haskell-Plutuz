HC7T3: Implement a function using multiple constraints
---


```haskell
-- compareValues function using type constraints
compareValues :: (Eq a, Ord a) => a -> a -> a
compareValues x y
    | x >= y    = x
    | otherwise = y

-- Main function to test compareValues
main :: IO ()
main = do
    print (compareValues 10 20)        -- Output: 20
    print (compareValues 'a' 'z')      -- Output: 'z'
    print (compareValues 3.14 2.71)    -- Output: 3.14
    print (compareValues "apple" "bat")-- Output: "bat"
```

---

### 📘 **Explanation**

#### ✅ Function Signature

```haskell
compareValues :: (Eq a, Ord a) => a -> a -> a
```

* `a` is a **type variable**.
* `(Eq a, Ord a) =>` means:

  * The type `a` must be an instance of **both `Eq` and `Ord`**.
  * `Eq` is needed for equality checks (like `==`, though not used here).
  * `Ord` is needed for comparison operators like `>=`.

---

#### ✅ Function Definition

```haskell
compareValues x y
    | x >= y    = x
    | otherwise = y
```





