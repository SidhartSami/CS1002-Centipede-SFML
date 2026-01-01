<a id="readme-top"></a>

[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<br />
<div align="center">
  <h3 align="center">Centipede Game</h3>

  <p align="center">
    A classic arcade shooter reimagined in C++ using SFML
    <br />
    <strong>Programming Fundamentals Project - Fall 2023</strong>
    <br />
    <strong>FAST-NUCES, Islamabad Campus</strong>
    <br />
    <br />
    <a href="https://github.com/sidhartsami/Centipede-Game"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/sidhartsami/Centipede-Game">View Demo</a>
    ·
    <a href="https://github.com/sidhartsami/Centipede-Game/issues/new?labels=bug&template=bug-report---.md">Report Bug</a>
    ·
    <a href="https://github.com/sidhartsami/Centipede-Game/issues/new?labels=enhancement&template=feature-request---.md">Request Feature</a>
  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
        <li><a href="#key-features">Key Features</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#game-mechanics">Game Mechanics</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

## About The Project

This is a faithful recreation of **Centipede**, the iconic arcade shooter originally released by Atari in June 1981. Built as a Programming Fundamentals project, this implementation captures the essence of the classic game while demonstrating fundamental programming concepts including 2D arrays, collision detection, object-oriented design, and game loop architecture.

The player controls a fighter spacecraft at the bottom of the screen, defending against waves of segmented centipedes, spiders, ants, and scorpions. Navigate through a field of destructible mushrooms while firing lasers to eliminate threats and rack up points across increasingly challenging levels.

### Key Features

**Core Gameplay:**
- **Grid-Based Architecture**: Game world represented using 2D array structure for efficient spatial management
- **Player Fighter**: Arrow key controls within a restricted 5-row high player zone at screen bottom
- **Dynamic Centipede AI**: 12-segment centipede that splits into multiple heads when damaged
- **Progressive Difficulty**: Speed increases with each level cleared
- **Intelligent Movement**: Centipedes move horizontally, descending when hitting mushrooms or screen edges

**Game Elements:**
- **Mushrooms**: 20-30 randomly placed obstacles requiring two hits to destroy
- **Poisonous Mushrooms**: Deadly obstacles spawned when centipedes die in player area
- **Multiple Enemy Types**: Centipede segments, spiders, ants, and scorpions
- **Collision Detection**: Precise hit detection for lasers, enemies, and obstacles
- **Audio Integration**: Background music and sound effects using SFML Audio

**Scoring System:**
- Mushroom Destruction: 1 point
- Centipede Body Segment: 10 points
- Centipede Head: 20 points
- High Score Persistence: Saved to `highscores.txt`

**Game Over Conditions:**
- Direct contact with centipede segments
- Collision with poisonous mushrooms

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

* [![C++][Cpp-badge]][Cpp-url]
* [![SFML][SFML-badge]][SFML-url]

**Key Technologies:**
- **C++** - Core game logic and OOP implementation
- **SFML 2.5+** (Simple and Fast Multimedia Library)
  - Graphics rendering
  - Window management
  - Audio playback
  - Event handling

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

### Prerequisites

Ensure you have the following installed on your system:

* **C++ Compiler** - GCC 7.0+ or Clang 5.0+
  ```sh
  # Ubuntu/Debian
  sudo apt-get install g++
  
  # macOS
  xcode-select --install
  ```

* **SFML 2.5 or higher**
  ```sh
  # Ubuntu/Debian
  sudo apt-get install libsfml-dev
  
  # macOS (using Homebrew)
  brew install sfml
  
  # Arch Linux
  sudo pacman -S sfml
  ```

### Installation

1. Clone the repository
   ```sh
   git clone https://github.com/sidhartsami/Centipede-Game.git
   ```

2. Navigate to the project directory
   ```sh
   cd Centipede-Game
   ```

3. Compile the game
   ```sh
   # Linux/macOS
   g++ Centipede.cpp -o centipede -lsfml-graphics -lsfml-window -lsfml-system -lsfml-audio
   
   # With optimization flags
   g++ -O2 Centipede.cpp -o centipede -lsfml-graphics -lsfml-window -lsfml-system -lsfml-audio
   ```

4. Run the executable
   ```sh
   ./centipede
   ```

**Note:** If you encounter linking errors, ensure SFML is properly installed and the library paths are configured correctly.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

### Controls

**Movement:**
- `↑` Arrow Up - Move fighter up (within player zone)
- `↓` Arrow Down - Move fighter down (within player zone)
- `←` Arrow Left - Move fighter left
- `→` Arrow Right - Move fighter right

**Combat:**
- `Space` - Fire laser

**Game Management:**
- `ESC` - Pause/Resume game
- `Q` - Quit to main menu

### Gameplay Tips

1. **Stay Mobile**: Keep moving to avoid centipede segments as they descend
2. **Create Paths**: Destroy mushrooms strategically to create clear lanes
3. **Target Heads**: Prioritize centipede heads for higher points (20 vs 10)
4. **Avoid Poison**: Stay away from poisonous mushrooms spawned in the player zone
5. **Plan Ahead**: Anticipate centipede movement patterns to position yourself optimally

### Game Progression

- **Level 1**: 12-segment centipede at base speed
- **Level 2+**: Increased centipede speed and more complex patterns
- Each level cleared adds to difficulty multiplier
- High scores are automatically saved

### Demo

A gameplay demonstration video (`GamePlay.mp4`) is included in the repository showcasing:
- Player movement and controls
- Centipede behavior and splitting mechanics
- Scoring system
- Level progression

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Game Mechanics

### Architecture

**Grid System:**
```cpp
// Game world represented as 2D array
const int GRID_WIDTH = 30;
const int GRID_HEIGHT = 30;
Cell grid[GRID_HEIGHT][GRID_WIDTH];
```

**Player Zone:**
- Restricted to bottom 5 rows of screen
- Boundary collision detection
- Laser firing with cooldown system

**Centipede Logic:**
```
Movement Pattern:
1. Move horizontally (left/right based on direction)
2. On collision with mushroom or edge:
   - Descend one row
   - Reverse direction
3. On laser hit:
   - Segment destroyed
   - Split into two separate centipedes if mid-body hit
   - Each new centipede becomes independent entity
```

**Collision Detection:**
- Pixel-perfect detection using SFML's sprite bounds
- Separate collision layers for:
  - Player vs Enemies
  - Lasers vs Enemies
  - Lasers vs Mushrooms
  - Player vs Poisonous Mushrooms

**Scoring Algorithm:**
```cpp
if (hit_mushroom) score += 1;
else if (hit_centipede_body) score += 10;
else if (hit_centipede_head) score += 20;
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

© 2023 Sidhart Sami – All Rights Reserved.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

**Sidhart Sami** - [LinkedIn](https://www.linkedin.com/in/sidhart-sami/) - [@sidhartsami](https://github.com/sidhartsami)

Project Link: [https://github.com/sidhartsami/Centipede-Game](https://github.com/sidhartsami/Centipede-Game)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Acknowledgments

- [SFML Documentation](https://www.sfml-dev.org/documentation/) - Essential multimedia library
- [Atari's Original Centipede](https://en.wikipedia.org/wiki/Centipede_(video_game)) - Game design inspiration
- [FAST-NUCES](https://www.nu.edu.pk/) - Academic institution
- [Game Programming Patterns](https://gameprogrammingpatterns.com/) - Design pattern reference
- [LazyFoo's SDL Tutorials](https://lazyfoo.net/tutorials/SDL/) - Game loop concepts

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[forks-shield]: https://img.shields.io/github/forks/sidhartsami/Centipede-Game.svg?style=for-the-badge
[forks-url]: https://github.com/sidhartsami/Centipede-Game/network/members
[stars-shield]: https://img.shields.io/github/stars/sidhartsami/Centipede-Game.svg?style=for-the-badge
[stars-url]: https://github.com/sidhartsami/Centipede-Game/stargazers
[issues-shield]: https://img.shields.io/github/issues/sidhartsami/Centipede-Game.svg?style=for-the-badge
[issues-url]: https://github.com/sidhartsami/Centipede-Game/issues
[license-shield]: https://img.shields.io/github/license/sidhartsami/Centipede-Game.svg?style=for-the-badge
[license-url]: https://github.com/sidhartsami/Centipede-Game/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/sidhart-sami/
[Cpp-badge]: https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white
[Cpp-url]: https://isocpp.org/
[SFML-badge]: https://img.shields.io/badge/SFML-8CC445?style=for-the-badge&logo=sfml&logoColor=white
[SFML-url]: https://www.sfml-dev.org/
