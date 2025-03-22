# Design and Test.

## Overview:

In this project, I was challenged to design a terminal printed "digital rain" in OOP programming style.
While undoubtably, it would be very much doable to write a one page script for this with the help of the internet.
Introducing the concepts of objects and inheritance pushed me to be more deliberate with how I went about programming.

# Researching:

The first thing I did with this project was research on the web "how to make a digital project in c++", while I found old git-hub repositories and some youtube videos, I never understood the core fundemental logic behind "how" the digital rain works or "why" it works like that.

I decided, I would prototype a project in Python.



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

## UML Diagram:

![UML Diagram](../assets/images/uml_diagram.png)

## Testing: