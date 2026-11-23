# tic-tac-toe

Tic-tac-toe in the browser, with two-player mode and two computer opponents, built for [The Odin Project](https://www.theodinproject.com/) curriculum.

**Live demo:** https://equanimity-studio.github.io/tic-tac-toe/

Built with HTML, CSS and vanilla JavaScript.

## Features

- Two players on one device, with editable player names
- **Robocop**, a computer opponent that picks random moves
- **Terminator**, a computer opponent that uses the **minimax algorithm** and can't be beaten
- Win and tie detection, and a Play Again button that swaps who goes first

## What I learned

- **The module pattern and factory functions**: the game board and display controller are each wrapped in an immediately invoked function (IIFE), and players are made by a `player()` factory, which keeps most variables out of the global scope
- **Recursion and game-tree search**: minimax tries every possible remaining move, scores each result (+10 for a win, -10 for a loss, 0 for a tie), and picks the best move
- **Event delegation**: one click listener on the document handles all nine squares
- **Refactoring as I went**: I moved from comparing square contents to tracking moves by board index, which made win checks and the AI much simpler

## Looking back: what I'd do differently

- **Track state in variables, not on screen.** Whether the computer is playing is worked out from the button text ("Play Computer") and the player's name ("Robocop"). A variable like `opponentType = "human" | "random" | "minimax"` would be clearer and wouldn't break if a label changed.
- **Write the turn logic once.** "Check for a win, check for a tie, switch players" is repeated in three places; it belongs in one `endTurn()` function.
- **Declare every variable.** `quadrant` and `roboChoice` are never declared with `let` or `const`, so they quietly become globals. Adding `"use strict"` or a linter would catch this.
- **Store the winning lines as data.** The win check spells out all eight lines in one long condition. A `WINNING_LINES` array checked in a loop is shorter and easier to verify.
