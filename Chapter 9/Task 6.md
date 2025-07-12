HC9T6: Define a Recursive Data Type

---


```haskell
-- Define a recursive Tweet data type
data Tweet = Tweet
    { content  :: String
    , likes    :: Int
    , comments :: [Tweet]  -- Recursive reference
    } deriving Show

-- Example tweet with nested comments
main :: IO ()
main = do
    let reply1 = Tweet "Nice post!" 3 []
    let reply2 = Tweet "Totally agree 🙌" 5 []
    let original = Tweet "Functional programming rocks!" 10 [reply1, reply2]

    print original
```

---

### 🧠 Explanation

- **Recursive Structure**:
  - The `comments` field is a list of `Tweet`, making this a **recursive data type**.
  - This allows tweets to have replies, which themselves can have replies, and so on.

- **Fields**:
  - `content :: String` — the text of the tweet.
  - `likes :: Int` — number of likes.
  - `comments :: [Tweet]` — a list of replies, recursively structured.

- **Sample Output**:

```
Tweet {content = "Functional programming rocks!", likes = 10, comments = [Tweet {content = "Nice post!", likes = 3, comments = []}, Tweet {content = "Totally agree 🙌", likes = 5, comments = []}]}
```

---

