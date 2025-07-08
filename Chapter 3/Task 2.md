HC3T2 - Task 2: Determine the grade based on a score using guards

```haskell
-- Function to assign a grade based on score using guards
grade :: Int -> String
grade score
    | score >= 90 = "A"
    | score >= 80 = "B"
    | score >= 70 = "C"
    | score >= 60 = "D"
    | otherwise   = "F"

-- Testing the function with some example scores
main :: IO ()
main = do
    print (grade 95)  -- Output: "A"
    print (grade 82)  -- Output: "B"
    print (grade 76)  -- Output: "C"
    print (grade 63)  -- Output: "D"
    print (grade 50)  -- Output: "F"
```

### 🧠 Explanation:

- The `grade` function takes an `Int` as input and returns a `String`.
- Guards (`|`) let you check conditions in order from top to bottom.
- `otherwise` is a built-in keyword that always evaluates to `True`—so it catches anything that didn’t match previous guards.

When you run this program, you'll see:

```
"A"
"B"
"C"
"D"
"F"
```




