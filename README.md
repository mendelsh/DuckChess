# 🦆 DuckChess

A Java-based implementation of **Duck Chess**, a chess variant where players must place a rubber duck on an empty square after each move. The duck acts as an obstacle that blocks piece movement and cannot be captured.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Game Rules](#game-rules)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [How to Play](#how-to-play)
- [Technical Details](#technical-details)
- [Dependencies](#dependencies)

## Overview

DuckChess is a graphical chess application built with Java Swing that implements the Duck Chess variant. In this variant, after each standard chess move, the player must place a rubber duck on any empty square. The duck cannot be moved or captured, making it a permanent obstacle that adds strategic depth to the game.

## Features

- **Full Chess Implementation**: All standard chess pieces with proper movement rules
  - Pawn (with en passant)
  - Rook
  - Knight
  - Bishop
  - Queen
  - King (with castling support)
- **Duck Mechanics**: After each move, place a duck on an empty square
- **Visual Interface**: Clean, modern GUI with chess piece graphics
- **Move Validation**: Comprehensive move validation for all piece types
- **Game State Management**: Tracks turn order, castling rights, and game completion
- **Chess Piece Graphics**: High-quality piece images for both white and black pieces
- **Custom Duck Icon**: Rubber duck image for the special duck piece

## Game Rules

### Standard Chess Rules (Modified for Duck Chess)
- All standard chess movement rules apply (piece movement, etc.)
- **No check or checkmate**: You win by capturing the opponent's king, not by delivering checkmate.
- **Castling**: Both kingside and queenside castling are supported
- **En Passant**: Pawn en passant captures are implemented
- **Pawn Promotion**: Pawns can promote to Queen, Rook, Bishop, or Knight when reaching the opposite end

### Duck Chess Specific Rules
1. After making a chess move, you **must** place the duck on an empty square
2. The duck cannot be moved or captured
3. The duck blocks all piece movement (pieces cannot move through or land on the duck)
4. The duck can be placed on any empty square on the board
5. If a move is invalid, the duck placement is also invalidated

## Getting Started

### Prerequisites

- **Java Development Kit (JDK)**: Version 8 or higher

### Running the Application

1. **Clone or download** this repository

2. **Compile the Java files**:
   ```bash
   javac src/*.java
   ```

3. **Run the application**:
   ```bash
   java -cp src Main
   ```

   Or from the `src` directory:
   ```bash
   cd src
   java Main
   ```

### Using an IDE

1. Open the project in your preferred Java IDE
2. Ensure the `src` directory is marked as the source root
3. Ensure `src/chessPieces` is included in the classpath (for image resources)
4. Run the `Main.java` file

## 📁 Project Structure

```
DuckChess/
├── README.md
└── src/
    ├── Main.java              # Entry point - initializes the visual board
    ├── Board.java             # Core game logic and board state management
    ├── VisualBoard.java       # GUI implementation using Java Swing
    ├── Bishop.java            # Bishop movement validation
    ├── King.java              # King movement and castling validation
    ├── Knight.java            # Knight movement validation
    ├── Pawn.java              # Pawn movement, en passant, and promotion
    ├── Rook.java              # Rook movement validation
    └── chessPieces/           # Chess piece images
        ├── Chess_bdt60.png    # Black bishop
        ├── Chess_blt60.png    # White bishop
        ├── Chess_kdt60.png    # Black king
        ├── Chess_klt60.png    # White king
        ├── Chess_ndt60.png    # Black knight
        ├── Chess_nlt60.png    # White knight
        ├── Chess_pdt60.png    # Black pawn
        ├── Chess_plt60.png    # White pawn
        ├── Chess_qdt60.png    # Black queen
        ├── Chess_qlt60.png    # White queen
        ├── Chess_rdt60.png    # Black rook
        ├── Chess_rlt60.png    # White rook
        └── rubber-duck.png    # Duck piece
```

## How to Play

1. **Start the game**: Run the application to open the chess board window
2. **Make a move**: 
   - Click on the piece you want to move
   - Click on the destination square
3. **Place the duck**: After your chess move, click on any empty square to place the duck
4. **Turn alternation**: The game automatically switches turns after a valid move and duck placement
5. **Win condition**: Capture the opponent's king to win

### Move Format

The game uses algebraic notation internally:
- Format: `[from][to]` (e.g., `e2-e4`)
- For duck placement: `[from][to],[duck]` (e.g., `e2-e4,h3`)
- For pawn promotion: `[from][to]=[piece],[duck]` (e.g., `e7-e8=q,h3`)

## Technical Details

### Core Components

#### `Board.java`
- Manages the 8x8 chess board state (represented as `char[][]`)
- Tracks turn order, castling rights, and game state
- Validates moves and handles special moves (castling, en passant, promotion)
- Manages duck placement and position tracking

#### `VisualBoard.java`
- Implements the GUI using Java Swing (`JFrame`, `JPanel`, `JButton`)
- Handles user interactions (click events)
- Loads and displays chess piece images
- Updates the visual representation after each move

#### Piece Classes (`Bishop.java`, `King.java`, `Knight.java`, `Pawn.java`, `Rook.java`)
- Each contains static `isValid()` methods for move validation
- Implements piece-specific movement rules
- Checks for obstacles (including the duck) in movement paths

### Key Features

- **Move Validation**: Each piece type has its own validation logic
- **Duck Blocking**: All pieces check for duck obstacles (`'D'`) in their paths
- **State Management**: Tracks king and rook movements for castling eligibility
- **Turn Management**: Alternates between white and black players
- **Game End Detection**: Detects when a king is captured

### Color Scheme

- **White squares**: `#e2e6ca` (light beige)
- **Black squares**: `#21788a` (teal blue)

## Dependencies

This project uses only **standard Java libraries**:

- `java.awt.*` - For colors and layout management
- `javax.swing.*` - For GUI components (JFrame, JPanel, JButton, ImageIcon)
- `java.util.HashMap` - For mapping piece characters to images

**No external dependencies required!** The project is self-contained and only requires a Java runtime environment.

## Future Enhancements

Potential improvements for future versions:
- [ ] Move history and undo functionality
- [ ] Save/load game state
- [ ] Computer AI opponent
- [ ] Online multiplayer support
- [ ] Move notation display
- [ ] Sound effects
- [ ] Theme customization

## 📝 License

This project is open source and available for educational purposes.

## 🤝 Contributing

Contributions are welcome! Feel free to submit issues, fork the repository, and create pull requests.

---

**Enjoy playing Duck Chess! 🦆♟️**
