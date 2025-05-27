# Blackjack AI

An advanced AI-driven implementation of Blackjack that learns and implements optimal strategies in Go.

## Overview

Blackjack AI extends the classic Blackjack game by incorporating artificial intelligence to both play optimally and learn from gameplay. The project demonstrates the implementation of customized AI options in the context of the popular card game Blackjack.

## Features

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
blackjack_ai

# Or run directly
go run github.com/laureanorios95/blackjack_ai
```

### Coding Options

```go
opts := blackjack.Options{
		Decks:           4,
		Hands:           999999,
		BlackjackPayout: 1.5,
	}
```

## Example Output

```
Balance
```


## Dependencies

This project uses:
- [github.com/laureanorios95/deck](https://github.com/laureanorios95/deck) - Card deck manipulation library
- [github.com/laureanorios95/blackjack](https://github.com/laureanorios95/blackjack) - Base blackjack game implementation

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
