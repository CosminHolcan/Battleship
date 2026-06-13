# Battleship Game

A classic Battleship naval combat game implementation featuring both graphical and text-based interfaces. Play against an intelligent AI opponent in this turn-based strategy game.

## Overview

This project is a fully functional implementation of the timeless Battleship game where you compete against a computer AI. The application provides two ways to play:
- **Graphical User Interface (GUI)** - Built with tkinter for an interactive visual experience
- **Text-Based Interface** - Command-line interface for terminal play

The AI opponent uses an intelligent hunting algorithm that adapts its strategy after hitting your ships, providing a challenging gameplay experience.

## How to Play

### Game Setup
1. **Place Your Ships**: You command a fleet of three ships:
   - **Battleship** - 4 squares long
   - **Cruiser** - 3 squares long
   - **Destroyer** - 2 squares long

2. **Computer Placement**: The AI automatically places its ships randomly on the board.

### Gameplay Rules
- The game board is an 8×8 grid with columns labeled A-H and rows numbered 0-7
- Players take turns attacking coordinates on the opponent's board
- **Hit (X)**: You successfully struck an opponent's ship
- **Miss (V)**: Your attack hit empty water
- **Win Condition**: First player to land all required hits (9 total) sinks the opponent's entire fleet and wins

### Playing via GUI
1. Use input fields to specify ship coordinates and direction during placement phase
2. Click grid squares to attack the computer's board
3. Watch real-time updates as battles unfold
4. Color-coded display shows:
   - Green: Your ships
   - Red: Hits
   - Purple: Sunken ships
   - Gray: Empty water

### Playing via Text Interface
1. Use menu commands to place ships and attack
2. View ASCII-formatted grids showing current board state
3. Enter coordinates in format: `A0` (column + row)

## GUI Features

The graphical interface provides:
- **Dual-Grid Display**: Side-by-side visualization of your board and opponent's board
- **Interactive Ship Placement**: Input fields for positioning each ship with direction selection
- **Real-Time Updates**: Immediate visual feedback on attacks and results
- **Status Display**: Current game state and turn information
- **Responsive Controls**: Easy-to-use buttons for game actions

The GUI is built using **tkinter** with support for background images and color-coded cell states for intuitive gameplay.

## Local Development

### Prerequisites
- Python 3.x
- pip (Python package manager)

### Installation

1. **Clone or navigate to the project directory**:
   ```bash
   cd Battleship
   ```

2. **Install required dependencies**:
   ```bash
   pip install pillow texttable
   ```

   - **Pillow**: For image processing in the GUI
   - **texttable**: For formatted table display in text interface

3. **Run the application**:
   ```bash
   python Main.py
   ```

### Project Structure

```
Domain.py          # Core game entity - Square class
Errors.py          # Custom exception classes
Repo.py            # Repository pattern for square collections
Validator.py       # Input validation for coordinates
Service.py         # Business logic and AI opponent
GUI.py             # Graphical user interface (tkinter)
UI.py              # Text-based user interface
Main.py            # Application entry point
Tests.py           # Unit tests
```

### Architecture

The project follows a **layered architecture pattern**:

```
GUI/UI Layer (GUI.py, UI.py)
    ↓
Service Layer (Service.py) - Game Logic & AI
    ↓
Repository Layer (Repo.py) - Data Management
    ↓
Domain Layer (Domain.py) - Game Entities
```

This design allows both interfaces to share the same game logic, ensuring consistency and maintainability.

## Technologies Used

### Core
- **Python 3.x** - Main programming language

### GUI
- **tkinter** - Python's standard GUI toolkit for the graphical interface
- **Pillow (PIL)** - Image processing for background images and graphics

### UI
- **texttable** - Formatted ASCII table generation for terminal display

### Development
- **Custom Exception Handling** - Domain-specific error classes
- **Repository Pattern** - Clean data access abstraction
- **Unit Tests** - Test suite for core functionality

## Computer Opponent

The computer opponent uses the following strategy:
1. **Random Targeting** - Initial attacks are random
2. **Hit Detection** - When the computer scores a hit, it remembers the location
3. **Hunting Mode** - The computer then systematically checks adjacent squares to find and destroy the entire ship
