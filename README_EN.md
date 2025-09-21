# Complex Root Calculator

An online calculator for computing n-th degree roots of numbers and complex mathematical expressions, with full support for complex numbers, trigonometric functions, and exponents.

### [🚀 View Live Demo](https://leus821.github.io/Complex-root-calculator/)


## ✨ Key Features

-   **N-th Degree Root Calculation**: Extracts roots of any integer degree (from 2 to 99).
-   **Expression Support**: Evaluates a mathematical expression before extracting the root.
-   **Complex Numbers**: Full support for the imaginary unit `i`.
-   **Functions and Exponents**: Handles `sin`, `cos`, and exponentiation via the `^` operator.
-   **Smart Input**: Real-time validation and formatting to prevent user errors.
-   **Customizable Precision**: Allows setting the number of decimal places for the result.
-   **Multilingual Support**: The interface can be switched between English and Russian.
-   **State Persistence**: Input data is saved to `localStorage` and restored on page reload.
-   **User-Friendly Interface**: Includes a virtual keyboard with navigation and auto-scrolling input fields.

---

## 🛠️ Tech Stack

-   **HTML5 / CSS3**: For the application's structure and styling.
-   **JavaScript (ES6+)**: Powers all application logic.
-   **Vite**: A modern, high-performance build tool and development server.
-   **Math.js**: A powerful math library for parsing and evaluating expressions.
-   **GitHub Pages**: For free project hosting and deployment.

---
---

## ⚙️ Installation and Local Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/leus821/Complex-root-calculator.git
    ```
2.  **Navigate to the project directory:**
    ```bash
    cd Complex-root-calculator
    ```
3.  **Install dependencies:**
    ```bash
    npm install
    ```
4.  **Start the development server:**
    ```bash
    npm run dev
    ```
    The project will be available at `http://localhost:5173`.

---

## 🧠 Core Logic and Function Descriptions

All primary application logic resides in `src/index.js`.

### The `App()` Function

This is the "heart" of the application. It runs once on startup and is responsible for:
1.  **Initialization**: Loading saved values from `localStorage` and immediately formatting them to clean up any invalid data.
2.  **Event Listener Setup**: Attaching all event handlers for buttons, input fields, and forms (`click`, `input`, `focus`, `blur`, `submit`).

### Formatting and Validation Functions

These functions enable the "smart input" feature and prevent user errors.

-   `formatInput(element)`: The most complex function, triggered on every change to the expression input field.
    1.  It uses a "whitelist" (`match`) to construct a new string containing only allowed tokens (numbers, `sin`, `cos`, `i`, `^`, operators).
    2.  It then applies a series of `replace` rules to fix invalid combinations, such as double operators (`++` -> `+`), operators after parentheses, or incorrect `^` usage (`sin^` -> `sin`).
    3.  It intelligently adjusts the cursor position to prevent it from jumping after auto-formatting.
    4.  Finally, it calls `scrollInputToEnd()` and `saveState()`.

-   `formatDegree()` & `formatAccuracy()`: Simple helper functions that strip all non-digit characters from the degree and precision input fields.

### DOM and State Management Functions

-   `saveState()`: Saves the current values from the expression and degree fields into `localStorage`.
-   `getCurrentElement()`: Determines which input field (`expression` or `degree`) is currently active based on the `.active` CSS class.
-   `insertAtCursor(element, text)`: Inserts text from the virtual keyboard at the current cursor position, rather than just at the end of the string.
-   `scrollInputToEnd(element)`: Forces the input field to scroll to the far right, ensuring the cursor is always visible when entering long expressions.
-   `clearResults()`: Clears the area where calculation results are displayed.

### The Calculation Function

-   `getResult(accuracyValue)`: The main function for performing calculations.
    1.  Retrieves values from the input fields.
    2.  Performs basic validation (e.g., ensures the expression doesn't end with a "+").
    3.  Uses a `try...catch` block to handle mathematical errors gracefully.
    4.  Calls `math.nthRoots(math.evaluate(...))` to first evaluate the expression and then extract the roots.
    5.  Formats the results to the specified precision and localizes the "Infinity" output.
    6.  Dynamically creates and injects HTML elements with the results onto the page.

---

## 🌐 Build and Deployment

The project is configured for easy deployment to GitHub Pages.

1.  **Build the project:**
    This command creates an optimized version of the site in the `dist` folder.
    ```bash
    npm run build
    ```
2.  **Deploy:**
    This command automatically pushes the contents of the `dist` folder to a special `gh-pages` branch on GitHub.
    ```bash
    npm run deploy
    ```
