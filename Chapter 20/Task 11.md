HC20T11: randomWalk with State Monad
Write a function randomWalk using the State monad that simulates a random walk on a 2D grid.
---

### ✅ **Working Haskell Code**

```haskell
module Main where

import Control.Monad.State
import System.Random (StdGen, mkStdGen, randomR)

-- | Position on a 2D grid
type Position = (Int, Int)

-- | Directions
data Direction = U | D | L | R deriving (Show, Enum, Bounded)

-- | Generate a random direction using the State monad
randomDirection :: State StdGen Direction
randomDirection = state $ \g ->
    let (i, g') = randomR (fromEnum (minBound :: Direction), fromEnum (maxBound :: Direction)) g
    in (toEnum i, g')

-- | Move from a position in a given direction
move :: Position -> Direction -> Position
move (x, y) U = (x, y + 1)
move (x, y) D = (x, y - 1)
move (x, y) L = (x - 1, y)
move (x, y) R = (x + 1, y)

-- | Take a single random step
randomStep :: Position -> State StdGen Position
randomStep pos = do
    dir <- randomDirection
    return (move pos dir)

-- | Perform n random steps starting from a position
randomWalk :: Int -> Position -> State StdGen [Position]
randomWalk 0 pos = return [pos]
randomWalk n pos = do
    nextPos <- randomStep pos
    rest <- randomWalk (n - 1) nextPos
    return (pos : rest)

-- | Example usage
main :: IO ()
main = do
    let gen = mkStdGen 42               -- deterministic seed
        walk = evalState (randomWalk 10 (0, 0)) gen
    putStrLn "Random Walk Path:"
    mapM_ print walk
```

---

### ✅ **Explanation**

1. **State Monad**

   * `State StdGen` threads a random number generator through the computation.
   * Each random step consumes part of the generator.

2. **Random Direction**

   * `randomDirection` picks a direction (`U`, `D`, `L`, `R`) randomly.

3. **Move Function**

   * Updates `(x, y)` coordinates based on the chosen direction.

4. **Recursive Walk**

   * `randomWalk n pos` recursively generates `n` steps, building a list of positions.

5. **Deterministic Example**

   * `mkStdGen 42` ensures reproducible results.

---


