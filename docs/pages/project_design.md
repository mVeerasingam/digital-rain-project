# Design and Test.

## Overview:

In this project, I was challenged to design a terminal printed "digital rain" in OOP programming style.
While undoubtably, it would be very much doable to write a one page script for this with the help of the internet.
Introducing the concepts of objects and inheritance pushed me to be more deliberate with how I went about programming.

# Researching and Prototyping:

Before diving into the C++ implementation, I researched existing approaches to digital rain simulations. While I found various GitHub repositories and YouTube tutorials in C++. However with this I found that I was focusing too much on the specifics of the language rather than the underlying logic. To address this, I decided to create a simple prototype in Python. The language's clear and readable syntax provided an ideal starting point for understanding the core mechanics of the simulation.

A key reference for my prototype was this YouTube tutorial:: [Digital Rain in Python](https://www.youtube.com/watch?v=eq-DoIjW4yI). I followed along with the tutorial in Python, using it as a guide to adapt the logic for the C++ implementation.


# Object-Oriented Approach:

The design approach I took for this project revolves around a "MatrixColumn" class, which represents individual cascading streams of characters of either "1" or "0". Each column behaves independently, following structured behaviors such as initialization, updating, and rendering to the terminal.

- Encapsulation: Each column maintains its own state, controlling the appearance and behavior of falling characters.

- Modularity: The MatrixColumn class is designed for reusability and can be instantiated multiple times to create the full digital rain effect.

- Abstraction: Helper functions such as shift_grid_down() and print_new_char() allow for cleaner and more manageable code.

My approach to this design was also influenced by my internship at Analog Devices, where I worked with an algorithm development team on C/C++ battery management systems. During that time, I gained experience in structuring algorithms using OOP principles, particularly in encapsulating logic and designing modular, extensible components—practices I applied to this project.

## UML Diagram:

![UML Diagram](../assets/images/uml_diagram.png)

## Testing Strategy
### Unit Testing
To ensure robustness, unit tests were implemented, focusing on core functionalities:
- **Constructor Test**: Verifies that `MatrixColumn` initializes correctly with given parameters.
- **Grid Initialization Test**: Ensures that the grid starts with expected values and raindrop distribution.
- **Update Method Test**: Checks whether characters shift properly and new ones are added at the top.
- **Boundary Conditions**: Tests behavior with empty or exceptionally large grids.
- **Character Generation Probability**: Ensures new raindrops appear based on the defined probability.

### Manual Testing
Given the graphical nature of the output, automated testing was supplemented with manual observation:
- **Visual Inspection**: Observing the terminal output to ensure characters flow correctly.
- **Boundary Testing**: Running the program with different terminal sizes to ensure proper rendering across various dimensions.
- **Performance Testing**: Checking for smooth rendering without excessive CPU usage, adjusting fields like delays, character printing probability and character spacing where necessary.