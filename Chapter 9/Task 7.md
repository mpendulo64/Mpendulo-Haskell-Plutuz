HC9T7: Implement a Function to Calculate Engagement

---



```haskell
-- Define the Tweet data type
data Tweet = Tweet
    { content  :: String
    , likes    :: Int
    , comments :: [Tweet]
    } deriving Show

-- Define a function to calculate total engagement
engagement :: Tweet -> Int
engagement (Tweet _ likeCount commentList) =
    likeCount + sum (map engagement commentList)

-- Example usage
main :: IO ()
main = do
    let reply1 = Tweet "Cool post!" 3 []
    let reply2 = Tweet "Love this 💯" 2 []
    let reply3 = Tweet "Check out my profile" 1 []
    let original = Tweet "Haskell is awesome!" 10 [reply1, reply2, reply3]

    print $ engagement original  -- Output: 16
```

---

### 🧠 Explanation

- **Recursive Design**:
  - The function takes one `Tweet`.
  - Adds its own `likes` to the sum of engagements from its `comments`.

- **`map engagement commentList`**:
  - Applies `engagement` recursively to each comment.
  - `sum` adds up all nested engagement values.



