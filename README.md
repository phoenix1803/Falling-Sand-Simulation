# p5.js Sketch: Falling Sand Simulation

This project is a p5.js sketch that simulates a color grid, where colors spread and move based on user input (mouse dragging). The grid cells change color dynamically, creating an abstract and colorful pattern. The sketch uses a basic simulation of particle-like behavior that reacts to the mouse's movements.

## Features

- **Grid of Squares**: The canvas is divided into a grid of squares, where each square can hold a color.
- **Color Cycling**: Each square’s color is chosen based on a hue value that increases over time, creating a dynamic color effect.
- **User Interaction**: When you drag the mouse across the grid, the color of the squares spreads around the mouse's position, creating a ripple effect.
- **Movement Simulation**: The color in each square "moves" to adjacent squares based on certain conditions, giving the appearance of color flowing and spreading.

## How to Use

1. **Drag the Mouse**: As you move the mouse across the canvas, colors will spread to the squares near the mouse position.
2. **Observe the Color Movement**: The squares will change color and create a flowing effect as the color transitions across the grid.
3. **Dynamic Hue**: As you keep dragging the mouse, the colors will gradually cycle through hues, providing a colorful, shifting grid.

## Logic

### 1. Grid Initialization
The grid is created as a 2D array of cells, where each cell can hold a color (initially set to `0` or no color). The width and height of each cell are set to `5` pixels.

In the `make2DArray` function, an array is created with columns and rows based on the canvas size. Each element in the array is initialized with a value of `0`.

### 2. User Interaction (mouseDragged)
When the mouse is dragged, we calculate which grid cell the mouse is over. For each cell near the mouse, a random chance is used to decide whether the cell should change color or not. The color is determined based on the current hue value (`hueValue`). The `hueValue` increases by `1` every time the mouse is dragged, cycling through different colors. If `hueValue` exceeds `360`, it resets back to 1.

The `matrix` variable defines the range of cells around the mouse that will change color. A random chance (`random(1) < 0.75`) is applied to each neighboring cell to decide whether to update its color.

### 3. Color Movement Simulation (draw)
In the `draw` function, a simulation of color movement takes place. For each cell, the current state (color) is checked. If the cell contains a color, the code checks the adjacent cells (below, left, and right). The color of the current cell "moves" to the neighboring cells if they are empty (no color). This gives the appearance of color flowing and spreading across the grid.

At each frame, a new grid is created (`nextGrid`) based on the previous grid's states, updating the colors and ensuring the movement of colors happens over time.

## Project Setup

To run this sketch, you need the following:

1. **Basic HTML Structure**: The sketch requires an HTML file that loads the p5.js library and your sketch file (`sketch.js`).
2. **p5.js Library**: p5.js is used to handle the canvas and rendering of the grid.

In your HTML file, link to the p5.js library and the sketch file:

- Link the p5.js library from the CDN: `<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>`
- Link your custom sketch file: `<script src="sketch.js"></script>`

### 3. Canvas Setup
In the `setup` function, the canvas is created with a width of `1690` pixels and height of `600` pixels. The color mode is set to HSB (Hue, Saturation, Brightness) for easy manipulation of colors. The number of columns and rows in the grid is calculated based on the canvas size and the width of each square (`w`).

### 4. Animation and Rendering
The `draw` function continuously updates the grid by checking the current state of each cell and moving colors based on the rules defined in the simulation. The colors are rendered to the canvas using the `fill` function with HSB values.

## Installation

To use this project locally:

1. Create an `index.html` file with the provided HTML structure.
2. Create a `sketch.js` file with the provided JavaScript code.
3. Open the `index.html` file in a web browser to see the sketch in action.
