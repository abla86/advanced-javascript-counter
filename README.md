# 🚀 Advanced JavaScript Counter

A progression-based JavaScript project that evolves the classic counter exercise into a more polished frontend application.

The project demonstrates practical JavaScript concepts including **DOM manipulation, event handling, persistent browser storage, keyboard controls, dynamic styling, animations, and accessibility improvements**.

It is designed both as a learning project and as a demonstration of frontend development skills.

---

## 🌐 Live Demo

GitHub Pages deployment coming next.

---

## ✨ Current Features

The current version includes:

- ➕ Increase counter
- ➖ Decrease counter
- 🔄 Reset counter
- 🔢 Support for positive and negative values
- 💾 Persistent state using `localStorage`
- ⌨️ Keyboard shortcuts
- 🎨 Dynamic color changes
- ✨ Animated number changes
- 🖱️ Interactive button effects
- ♿ ARIA labels and live counter updates
- 📱 Responsive layout
- ⚡ Vanilla JavaScript with no external dependencies

---

## 🖥️ How It Works

The application maintains the current counter value in JavaScript and updates the DOM whenever the value changes.

The value is also stored using the browser's **Web Storage API**, allowing the counter to survive page reloads.

```javascript
const savedCount = Number.parseInt(
  localStorage.getItem("count"),
  10
);

let count = Number.isNaN(savedCount)
  ? 0
  : savedCount;

  Whenever the counter changes, the application:

Updates the displayed value
Changes the number color
Saves the new value to localStorage
Triggers a short animation
⌨️ Keyboard Controls

The counter can be controlled without using the mouse.

Key	Action
+	Increase
Arrow Up	Increase
-	Decrease
Arrow Down	Decrease
R	Reset
Escape	Reset

Keyboard events are handled using JavaScript event listeners:

document.addEventListener("keydown", (event) => {
  if (event.key === "+" || event.key === "ArrowUp") {
    increase();
  }

  if (event.key === "-" || event.key === "ArrowDown") {
    decrease();
  }

  if (
    event.key.toLowerCase() === "r" ||
    event.key === "Escape"
  ) {
    reset();
  }
});
🎨 Dynamic Styling

The counter provides visual feedback based on its value:

Green — positive value
Red — negative value
Black — zero
if (count > 0) {
  display.style.color = "green";
} else if (count < 0) {
  display.style.color = "red";
} else {
  display.style.color = "black";
}

This provides immediate visual feedback while demonstrating dynamic DOM styling.

✨ Animation

Each counter change triggers a small scale animation.

#count {
  transition:
    transform 0.2s ease,
    color 0.3s ease;
}

#count.bump {
  transform: scale(1.25);
}

JavaScript temporarily applies the animation class whenever the value changes.

This demonstrates the interaction between JavaScript state changes and CSS transitions.

💾 LocalStorage Persistence

The application stores the current counter value in the browser:

localStorage.setItem("count", count);

When the page is reopened or refreshed, the stored value is restored.

This demonstrates basic client-side persistence without requiring a database or backend.

♿ Accessibility

Accessibility improvements include:

<h2 id="count" aria-live="polite">0</h2>

<button
  id="dec"
  aria-label="Decrease counter">
  −
</button>

<button
  id="reset"
  aria-label="Reset counter">
  Reset
</button>

<button
  id="inc"
  aria-label="Increase counter">
  +
</button>

The project currently demonstrates:

ARIA labels
Live region updates
Native HTML buttons
Keyboard interaction
Clear visual feedback

These features improve accessibility while introducing practical accessibility concepts.

🌱 Learning Progression

The project builds on the classic beginner JavaScript counter.

1️⃣ Basic Counter

A basic counter introduces:

Variables
Functions
DOM manipulation
Button interaction

Example:

let count = 0;

function update() {
  document.getElementById("count").textContent = count;
}

function increase() {
  count++;
  update();
}

function decrease() {
  count--;
  update();
}

This establishes the basic relationship between JavaScript state and the DOM.

2️⃣ Advanced Counter

The current implementation extends the basic counter with:

addEventListener
LocalStorage persistence
Keyboard controls
Reset functionality
Negative values
Dynamic styling
CSS animations
Accessibility improvements
Responsive UI

This turns the original learning exercise into a more complete frontend project.

🌟 Advanced Improvements

The project can continue evolving through several additional frontend concepts.

3️⃣ Multiple Counters
Why it matters

Multiple counters demonstrate reusable logic, scalable DOM structures, and component-like behaviour.

Example:

<div class="counter">
  <h3 id="count-1">0</h3>
  <button data-counter="1" data-change="1">+</button>
  <button data-counter="1" data-change="-1">-</button>
</div>

<div class="counter">
  <h3 id="count-2">0</h3>
  <button data-counter="2" data-change="1">+</button>
  <button data-counter="2" data-change="-1">-</button>
</div>

Possible reusable logic:

const counters = {
  1: 0,
  2: 0
};

function change(id, delta) {
  counters[id] += delta;

  document.getElementById(
    `count-${id}`
  ).textContent = counters[id];
}
What this demonstrates
Reusable logic
Dynamic DOM selection
Scalable multi-counter behaviour
Separation between data and presentation
4️⃣ ES6 Modules

A future refactor can separate application logic from DOM logic.

counter.js
export function createCounter(start = 0) {
  let value = start;

  return {
    increase() {
      value++;
      return value;
    },

    decrease() {
      value--;
      return value;
    },

    reset() {
      value = 0;
      return value;
    },

    get() {
      return value;
    }
  };
}
main.js
import { createCounter } from "./counter.js";

const counter = createCounter();

document
  .getElementById("inc")
  .addEventListener("click", () => {
    update(counter.increase());
  });
HTML
<script type="module" src="main.js"></script>
What this demonstrates
ES6 import / export
Separation of concerns
Reusable application logic
Modern JavaScript architecture
5️⃣ Multiple Counters & Modular Architecture

Combining reusable counter objects with ES6 modules would allow several independent counters to use the same underlying logic.

This represents the next architectural step from a single-page learning exercise toward a more structured frontend application.

6️⃣ React Component

The same counter concept can later be implemented using React.

import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h2>{count}</h2>

      <button
        onClick={() => setCount(count + 1)}
      >
        +
      </button>

      <button
        onClick={() => setCount(count - 1)}
      >
        -
      </button>

      <button
        onClick={() => setCount(0)}
      >
        Reset
      </button>
    </div>
  );
}
What this demonstrates
React state
useState
Declarative UI
Component architecture
Event handling in React
7️⃣ Unit Testing

Separating counter logic makes it possible to test behaviour independently of the UI.

Example:

counter.js
export function increase(n) {
  return n + 1;
}

export function decrease(n) {
  return n - 1;
}
Example test
test("increase adds 1", () => {
  expect(increase(0)).toBe(1);
});

test("decrease subtracts 1", () => {
  expect(decrease(1)).toBe(0);
});
What this demonstrates
Testable architecture
Automated verification
Predictable application behaviour
Separation of business logic from the DOM
8️⃣ Further Accessibility Improvements

Future accessibility work can include:

Visible keyboard focus indicators
prefers-reduced-motion
Automated accessibility testing
Manual keyboard testing
Screen-reader testing
Improved semantic structure
Contrast verification

Accessibility is treated as an ongoing development consideration rather than a one-time feature.

🛠️ Technologies
Currently used
HTML5
CSS3
JavaScript
DOM API
Web Storage API (localStorage)
ARIA
Planned / Learning Roadmap
ES6 Modules
Automated testing
React
TypeScript
GitHub Actions
📂 Project Structure

The current project intentionally uses a simple structure:

advanced-javascript-counter/
├── index.html
└── README.md

HTML, CSS and JavaScript are currently contained in a single file.

This keeps the initial implementation simple while allowing the project to be refactored into modules as it develops.

🚀 Getting Started

Clone the repository:

git clone https://github.com/abla86/advanced-javascript-counter.git

Open the project:

cd advanced-javascript-counter

Then open:

index.html

in a modern web browser.

No installation, package manager or external dependencies are required for the current version.

🧭 Roadmap
 Basic counter concept
 Increment and decrement
 Reset functionality
 Negative values
 Event listeners
 Keyboard controls
 LocalStorage persistence
 Dynamic styling
 CSS animation
 Accessibility improvements
 Responsive layout
 Multiple independent counters
 ES6 module refactor
 Automated unit tests
 React implementation
 TypeScript rewrite
 GitHub Pages live demo
 GitHub Actions CI pipeline
🎯 Project Purpose

This project is part of a practical frontend learning portfolio.

Rather than stopping at a basic counter tutorial, the project demonstrates how a simple application can gradually evolve by introducing:

state → DOM manipulation → events → persistence → keyboard interaction → animation → accessibility → modular architecture → testing → frameworks

The goal is to document both the working application and the development progression behind it.

📜 License

MIT License — free to use, modify and share.