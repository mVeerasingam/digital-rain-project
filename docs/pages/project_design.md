# Design and Test.

## Overview:

In this project, I was challenged to design a terminal printed "digital rain" in OOP programming style.
While undoubtably, it would be very much doable to write a one page script for this with the help of the internet.
Introducing the concepts of objects and inheritance pushed me to be more deliberate with how I went about programming.

# Researching and Prototyping:

Before diving into the C++ implementation, I researched existing approaches to digital rain simulations. While I found various GitHub repositories and YouTube tutorials, many lacked clear explanations of the underlying logic. To bridge this gap, I first prototyped the effect using Python, which allowed for rapid iteration and a deeper understanding of how cascading characters should behave.

A major reference for my prototype was this YouTube tutorial: [Digital Rain in Python](https://www.youtube.com/watch?v=eq-DoIjW4yI).

I followed a long with this tutorial in python, letting it be the reference for how I would adopt it to C++.

# Design Approach:

We have convered Object-Oriented Porgramming (OOP) extensivley throughout this course in ATU. However this is the first time we have used OOP in an algorithmic development setting.

However, this challenge of blending OOP to algorithms, is somethin I have person experience with during my internship at Analog Devices, where I worked with an Algorithms Development Group on C/C++ battery management systems. From my internship, I was collaberating on designing a battery "state of charge" algorithm in OOP fashion, through that I learnt the importance of 
- Abstracting features like initualizing the algorithm state or when you want to update the algorithm.
- Encapsulating the core algorithm logic so that we can inherit from other classes that would feed into the algorithm.

With all this in mind...

The design approach I took for this project revolves around a "MatrixColumn" class, which represents individual cascading streams of characters of either "1" or "0". Each column behaves independently, following structured behaviors such as initialization, updating, and rendering to the terminal. The implementation ensures:

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
- **Performance Testing**: Checking for smooth rendering without excessive CPU usage, adjusting delays where necessary.
- **Code Robustness**: Ensuring that changes to class properties (such as the activation probability or character set) affect the rain effect as expected.
