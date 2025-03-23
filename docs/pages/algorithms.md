# **Algorithms**

The digital rain effect creates a smooth stream of falling characters. It uses a few key algorithms to achieve this effect by simulating falling characters using 1D arrays. Each column of characters is represented as an array, and these arrays are updated and printed at their respective positions to create the cascading effect seen in the Matrix.

---

## **Overview**

The effect is achieved by simulating columns of characters in 1D arrays, where each column is displayed at a fixed **x-position** on the console. The columns update by shifting characters down and adding new characters at the top. This creates the falling effect.

---

## **Algorithm Breakdown**

### **1. Representing a Column Using a 1D Array**

Each column of characters is stored in a **1D array** (`grid`). Each element of the array represents a character at a specific row in the column:

```
grid[0]  →  Top of the column (new characters appear here)
grid[1]
grid[2]
...
grid[n-1]  →  Bottom of the column (characters disappear here)
```

Each column is displayed at a fixed x-position, and the characters are printed at their corresponding (x, y) positions.

### **2. Updating the Column**

Each frame follows these steps:

1. **Shift characters downward:**  
   - Move every character one position lower in the grid.
   - The bottommost character is lost, and the topmost position becomes empty.

2. **Generate a new character at the top:**  
   - Randomly insert a character (`'1'` or `'0'`) with a certain probability.
   - Otherwise, leave the top position empty for variation.

3. **Print the updated column:**  
   - Iterate through the grid array and print each character at its corresponding (x, y) position on the screen.

---

### **3. Displaying Multiple Columns**

To create the full-screen effect, multiple columns are placed across the terminal. These columns operate independently, with random character generation ensuring variation.

The digital rain loop continuously updates and prints all columns:

```
while (true) {
    for (auto& column : columns) {
        column.update();  // Shift and add new characters
    }
    std::cout.flush();  // Smooth display
    std::this_thread::sleep_for(std::chrono::milliseconds(50));  // Control speed
}
```