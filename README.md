# Blackjack AI

An advanced AI-driven implementation of Blackjack that learns and implements optimal strategies in Go.

## Overview

Blackjack AI extends the classic Blackjack game by incorporating artificial intelligence to both play optimally and learn from gameplay. The project demonstrates the implementation of various AI techniques including reinforcement learning, basic strategy, and card counting systems in the context of the popular card game Blackjack.

## Features

- AI players implementing different strategies:
  - Basic Strategy implementation
  - Card counting systems (Hi-Lo, KO, Omega II, etc.)
  - Reinforcement learning models
- Training mode to improve AI performance over time
- Performance analysis and strategy comparison tools
- Simulation capabilities to run thousands of hands for statistical analysis
- Visualization of winning probabilities and earnings over time
- Customizable AI parameters and learning rates
- Benchmark tools to evaluate strategy effectiveness

## Installation

```bash
go get github.com/laureanorios95/blackjack_ai
```

## Usage

### Running a Basic Simulation

```bash
# Install and run
go install github.com/laureanorios95/blackjack_ai
blackjack_ai -hands=10000 -strategy=basic

# Or run directly
go run github.com/laureanorios95/blackjack_ai -hands=10000 -strategy=basic
```

### Command-line Options

```bash
blackjack_ai -strategy=hilow    # Use Hi-Lo card counting system
blackjack_ai -learn=true        # Enable learning mode
blackjack_ai -decks=6           # Use 6 decks (casino standard)
blackjack_ai -bankroll=1000     # Start with $1000
blackjack_ai -bet-spread=1-12   # Use bet spread from 1-12 units
blackjack_ai -export=stats.json # Export results to JSON file
```

## AI Strategies

### Basic Strategy

Implements the mathematically optimal decisions for each player hand versus dealer upcard, without card counting.

```bash
blackjack_ai -strategy=basic
```

### Card Counting Systems

```bash
# Hi-Lo system
blackjack_ai -strategy=hilow

# Knockout (KO) system
blackjack_ai -strategy=ko

# Omega II system
blackjack_ai -strategy=omega2
```

### Reinforcement Learning

```bash
# Train a new model
blackjack_ai -strategy=rl -train=true -episodes=1000000

# Use a pre-trained model
blackjack_ai -strategy=rl -model=path/to/model.json
```

## Example Output

```
Blackjack AI Simulation Results
==============================
Strategy: Hi-Lo Card Counting
Hands played: 10,000
Decks: 6
Initial bankroll: $1,000
Final bankroll: $1,247.50
Return: +24.75%

Performance by true count:
TC ≤ -1:  -5.2% (1,423 hands)
TC = 0:   -0.8% (4,102 hands)
TC = +1:  +2.1% (2,711 hands)
TC = +2:  +5.7% (1,203 hands)
TC = +3:  +11.2% (431 hands)
TC ≥ +4:  +17.8% (130 hands)

Advantage charting:
Average bet: $15.24
SCORE: 0.78% per hand
Risk of Ruin: 2.3%
```

## Project Structure

```
blackjack_ai/
├── main.go                # Entry point
├── ai/                    # AI implementations
│   ├── strategy.go        # Strategy interface
│   ├── basic.go           # Basic strategy
│   ├── counting/          # Card counting systems
│   │   ├── hilow.go
│   │   ├── ko.go
│   │   └── omega2.go
│   └── reinforcement/     # Reinforcement learning
│       ├── model.go
│       ├── training.go
│       └── agent.go
├── game/                  # Game logic
│   ├── game.go
│   ├── table.go
│   └── rules.go
├── simulation/            # Simulation tools
│   ├── simulator.go
│   ├── analysis.go
│   └── reporting.go
├── util/                  # Utility functions
│   └── statistics.go
└── viz/                   # Visualization tools
    ├── chart.go
    └── terminal.go
```

## Dependencies

This project uses:
- [github.com/laureanorios95/deck](https://github.com/laureanorios95/deck) - Card deck manipulation library
- [github.com/laureanorios95/blackjack](https://github.com/laureanorios95/blackjack) - Base blackjack game implementation
- [gonum.org/v1/gonum](https://github.com/gonum/gonum) - Numerical computing library for statistics

## Research and Documentation

The strategies implemented in this project are based on well-established blackjack research and literature:

- Basic Strategy is based on computer simulations that identify the optimal play for any player hand against any dealer upcard
- Card counting systems are implemented according to their published specifications
- The reinforcement learning models use Q-learning and neural networks to develop strategies from scratch

## Advanced Usage

### Creating a Custom Strategy

```go
import "github.com/laureanorios95/blackjack_ai/ai"

// Implement the Strategy interface
type MyCustomStrategy struct {
    // Custom fields
}

// Implement decision method
func (s *MyCustomStrategy) DecideAction(playerHand []deck.Card, dealerUpcard deck.Card, 
                                        count float64, trueCount float64) game.Action {
    // Custom logic
    return game.Hit
}

// Use your custom strategy
sim := simulation.New(
    simulation.WithStrategy(&MyCustomStrategy{}),
    simulation.WithHands(10000),
)
results := sim.Run()
```

### Exporting Learning Data

```bash
# Export reinforcement learning data
blackjack_ai -strategy=rl -train=true -episodes=100000 -export-model=mymodel.json

# Export simulation results for analysis
blackjack_ai -strategy=hilow -hands=1000000 -export=results.csv
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

Jon Calhoun - [gophercises.com](https://gophercises.com/)

## Acknowledgments

- Based on research by Edward O. Thorp, Stanford Wong, and other blackjack mathematicians
- Inspired by the blackjack exercises from Gophercises
- Thanks to all contributors and testers
