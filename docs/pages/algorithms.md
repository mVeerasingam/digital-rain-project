# Algorithms

The digital rain effect relies on several key algorithms to create a smooth, cascading stream of characters. Below, I break down the main algorithms used in my implementation, explaining their role and how they contribute to the overall effect.

## Overview:
The core idea behind the digital rain effect is simulating falling characters using 1D arrays, where each column of characters is represented as a single array. By continuously updating and printing these arrays at their respective "x-positions", we achieve the cascading effect seen in the Matrix digital rain.

Each MatrixColumn object maintains a 1D array (grid), which stores the characters currently displayed in that column. The simulation works by updating these arrays over time, shifting characters downward and adding new ones at the top.

# Algorithm Breakdown:

## 1. Representing a Column Using a 1D Array
Each column of falling characters is stored as a 1D array (grid), where each element represents a character at a specific row in the column:

```
grid[0] -> Top of the column (new characters appear here)
grid[1]
grid[2]
...
grid[n-1] -> Bottom of the column (characters disappear here)
```

The column is displayed vertically at a fixed x-position on the console. When printing the column, each element of the array is placed at the corresponding (x, y) position.

## 2. Updating the Column
Each frame of the animation follows these three key steps:

- 1) Shift all characters downward

    - Move every character one position lower in the grid array.

    - The bottommost character is lost, and the topmost position becomes empty.

- 2) Generate a new character at the top

    - With a certain probability (ACTIVATION_PROBABILITY), randomly insert a new character ('1' or '0').

    - Otherwise, leave the top empty for variation.

- 3) Print the updated column to the console
    - Iterate through the grid array and set the cursor at (columnXPosition, y).
    - Print the character at grid[y] in its corresponding row.

## 3. Displaying Multiple Columns
To create a full-screen effect, multiple MatrixColumn objects are placed across the terminal width at evenly spaced x-positions. These columns operate independently, each updating at its own pace due to randomized character generation.

The digital rain loop continuously updates all columns and prints them to the console in real-time:

```
while (true) {
    for (auto& column : columns) {
        column.update(); // Shift and add new characters
    }
    std::cout.flush(); // Ensure smooth display
    std::this_thread::sleep_for(std::chrono::milliseconds(50)); // Control speed
}
```

# Detailed Breakdown:

## 1. Grid Initialization 
File: `matrixColumn.cpp`
Function: `init_column()`

Before the simulation begins, each column of falling characters must be initialized. The algorithm randomly decides which positions in the column will start with a raindrop (either '1' or '0').

Steps:

- Loop through each row in the column.

- Generate a random number and compare it to a probability threshold (ACTIVATION_PROBABILITY).

- If the probability condition is met, place a character ('1' or '0') in that row; otherwise, leave it blank.

- This initialization ensures that the simulation does not start with an empty screen, giving the effect an organic, unpredictable look.

# 2. Character Falling Algorithm
File: `matrixColumn.cpp`
Function: `shift_grid_down()`

This algorithm moves all characters in a column downward, creating the visual effect of falling rain.

Steps:

- Start from the bottom of the column and iterate upwards.

- Shift each character down one position.

- The topmost position is left blank for new characters to be introduced.

- This simple yet effective approach ensures that characters cascade naturally down the screen.

# 3. New Character Generation Algorithm
File: `matrixColumn.cpp`
Function: `print_new_char()`

To keep the effect dynamic, new characters must continuously appear at the top of each column. This algorithm determines whether a new character should appear and, if so, which character to use.

Steps:

Generate a random number and compare it to the activation probability.

If the probability condition is met, randomly select a '1' or '0' and place it at the top of the column.

Otherwise, leave the top row empty to maintain variation.

This randomness prevents uniformity, making the effect feel more like natural rain rather than a predictable pattern.


# 4. Multi-Column Rendering Algorithm
File: `digitalRain.cpp`
Function: `ExecuteDigitalRain()`

This algorithm ensures that multiple columns of characters are displayed and updated in a synchronized manner.

Steps:

- Determine the terminal's width and height.

- Create MatrixColumn objects at evenly spaced x-positions.

- Enter a continuous loop where:

- Each column updates its state (falling characters).

- The screen is refreshed to reflect the changes.

- Introduce a short delay for smoother animation.

By spacing the columns out evenly and updating them continuously, this algorithm ensures a cohesive and visually appealing digital rain effect.