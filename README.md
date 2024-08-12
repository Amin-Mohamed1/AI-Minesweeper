# Minesweeper Game

## Project Description

This project implements a Minesweeper game with an AI player. The game is played on an 8x8 grid where some cells contain hidden mines. The player's objective is to uncover all safe cells without triggering any mines. The AI player makes logical decisions based on available information, marking cells as safe or containing mines and updating its knowledge as more of the board is revealed.

## Files

- **`minesweeper.py`**: Contains the main classes and logic for the Minesweeper game and the AI player.
- **`runner.py`**: Provides a graphical implementation using Pygame, including user interaction, AI integration, and game state management.

## Classes

### Minesweeper

- **Attributes:**
  - `height`: The height of the board.
  - `width`: The width of the board.
  - `mines`: A set containing the positions of the mines.
  - `board`: A 2D list representing the game board, where `True` indicates a mine and `False` indicates no mine.
  - `mines_found`: A set of mines identified by the player.
  
- **Methods:**
  - `__init__(self, height=8, width=8, mines=8)`: Initializes the game board and randomly places mines.
  - `print(self)`: Prints the current state of the board with mines shown.
  - `is_mine(self, cell)`: Checks if a given cell contains a mine.
  - `nearby_mines(self, cell)`: Counts the number of mines around a given cell.
  - `won(self)`: Checks if the player has won by flagging all the mines.

### Sentence

- **Attributes:**
  - `cells`: A set of board cells.
  - `count`: The number of mines among the `cells`.
  
- **Methods:**
  - `__init__(self, cells, count)`: Initializes the sentence with a set of cells and a mine count.
  - `__eq__(self, other)`: Checks if two sentences are equal.
  - `__str__(self)`: Returns a string representation of the sentence.
  - `__hash__(self)`: Returns the hash value of the sentence.
  - `known_mines(self)`: Returns the set of all cells in `self.cells` known to be mines.
  - `known_safes(self)`: Returns the set of all cells in `self.cells` known to be safe.
  - `mark_mine(self, cell)`: Marks a cell as a mine in the sentence.
  - `mark_safe(self, cell)`: Marks a cell as safe in the sentence.

### MinesweeperAI

- **Attributes:**
  - `height`: The height of the board.
  - `width`: The width of the board.
  - `moves_made`: A set of cells where the AI has made moves.
  - `mines`: A set of cells identified by the AI as mines.
  - `safes`: A set of cells identified by the AI as safe.
  - `knowledge`: A list of sentences representing the AI's knowledge of the game board.
  
- **Methods:**
  - `__init__(self, height=8, width=8)`: Initializes the AI player.
  - `mark_mine(self, cell)`: Marks a cell as a mine and updates the AI's knowledge.
  - `mark_safe(self, cell)`: Marks a cell as safe and updates the AI's knowledge.
  - `add_knowledge(self, cell, count)`: Updates the AI's knowledge base after uncovering a safe cell.
  - `make_safe_move(self)`: Returns a safe cell for the AI to move to.
  - `make_random_move(self)`: Returns a random cell for the AI to move to, avoiding known mines.

## Imports

- `pygame`: The main library used for game development.
- `sys`: Used for system-level operations such as exiting the program.
- `time`: Provides time-related functions.

## Constants

- `HEIGHT`: Number of rows in the Minesweeper grid.
- `WIDTH`: Number of columns in the Minesweeper grid.
- `MINES`: Number of mines on the board.

## Colors

- `BLACK`: Color used for the background.
- `GRAY`: Color used for the cell background.
- `WHITE`: Color used for text and cell borders.

## Pygame Initialization

- Initializes Pygame and sets up the game window size to 600x400 pixels.
- Defines fonts for text rendering.

## Board Configuration

- Computes the dimensions of the game board and individual cells based on the window size.
- Loads and scales images for flags and mines.

## Game and AI Setup

- Creates instances of the `Minesweeper` game and `MinesweeperAI` agent.
- Initializes sets to keep track of revealed cells, flagged cells, and game state (win/loss).

## Game Loop

- **Event Handling:** Checks for quit events and updates game state based on user interactions.
- **Instructions Display:** Shows game instructions and a "Play Game" button at the start.
- **Board Drawing:** Draws the Minesweeper grid, including cells, flags, and mines.
- **Button Drawing:** Adds buttons for AI moves and game reset, and displays game status (won/lost).
- **User Interaction:** Handles user clicks for revealing cells or placing flags, and makes AI moves if requested.
- **Game Update:** Processes user and AI moves, updating the game state and AI knowledge.

## Key Functions

- **Event Handling:** Detects and processes user input (mouse clicks) for game actions.
- **Board Drawing:** Renders the Minesweeper board and updates the display based on game state.
- **AI Moves:** Allows the AI to make safe or random moves and updates its knowledge of the game state.

## Requirements

- Pygame library (`pip install pygame`)
- Custom `minesweeper` module with `Minesweeper` and `MinesweeperAI` classes
- Images for flags and mines
- Font file (`OpenSans-Regular.ttf`)
