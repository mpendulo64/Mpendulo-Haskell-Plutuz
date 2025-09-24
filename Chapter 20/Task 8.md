HC20T8: Parser Monad for Simple Expressions
Build a parser that parses simple expressions using the Parser monad.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Text.Parsec
import Text.Parsec.String (Parser)

-- | Parse an integer
integer :: Parser Int
integer = read <$> many1 digit

-- | Parse an expression with addition and multiplication
expr :: Parser Int
expr = term `chainl1` addOp

-- | Parse a term (handles multiplication)
term :: Parser Int
term = factor `chainl1` mulOp

-- | Parse a factor (either an integer or a parenthesized expression)
factor :: Parser Int
factor = integer <|> between (char '(') (char ')') expr

-- | Parse addition operator
addOp :: Parser (Int -> Int -> Int)
addOp = do
    _ <- spaces
    _ <- char '+'
    _ <- spaces
    return (+)

-- | Parse multiplication operator
mulOp :: Parser (Int -> Int -> Int)
mulOp = do
    _ <- spaces
    _ <- char '*'
    _ <- spaces
    return (*)

-- | Function to run the parser
parseExpression :: String -> Either ParseError Int
parseExpression = parse (spaces *> expr <* eof) ""

main :: IO ()
main = do
    print $ parseExpression "2+3"          -- Right 5
    print $ parseExpression "2+3*4"        -- Right 14 (multiplication first)
    print $ parseExpression "(2+3)*4"      -- Right 20 (parentheses first)
    print $ parseExpression "10*2+5*3"     -- Right 35
    print $ parseExpression "42"           -- Right 42
```

---

### ✅ **Explanation**

1. **Parser Monad**

   * The `Parser` type is a monad that consumes input and either **produces a result** or **fails with an error**.
   * This allows us to combine smaller parsers into bigger ones elegantly.

2. **Grammar Definition**
   We are implementing this grammar (with precedence):

   ```
   expr   = term ('+' term)*        -- Addition (lowest precedence)
   term   = factor ('*' factor)*    -- Multiplication (higher precedence)
   factor = integer | '(' expr ')'  -- Numbers or parenthesized sub-expressions
   ```

   * `chainl1` is used to parse left-associative binary operations.

3. **Whitespace Handling**

   * We explicitly consume spaces around operators to allow input like `"2 + 3 * 4"`.

4. **Error Handling**

   * `parseExpression` returns `Either ParseError Int`.
   * If parsing fails, you get a descriptive error message from Parsec.

---
---

### ✅ **Why This is Powerful**

* The **Parser monad** makes it easy to build complex parsers compositionally.
* We can easily extend this:

  * Add subtraction (`-`) and division (`/`)
  * Add support for unary minus
  * Add variables and assignments
  * Add floating-point numbers

---

