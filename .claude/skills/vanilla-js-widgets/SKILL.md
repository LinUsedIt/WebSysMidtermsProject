---
name: vanilla-js-widgets
description: Use this skill whenever you write or edit script.js or any JavaScript, build the interactive widget (slider, zoom comparison, RLE encoder/decoder demo, audio synth), build the quiz page, handle clicks or input, or touch the DOM. Use it for any JavaScript task, even a one-line event listener. Keep the code simple because the user is still learning JS.
---

# Vanilla JS Widgets

## Style (the user is new to JS and must explain this code)
- Plain JavaScript only. No frameworks, no build step.
- `const` by default, `let` when it changes. Never `var`.
- Small named functions, one job each. A short comment above every function and every block.
- Descriptive names (`encodeRLE`, `updateZoom`), no one-letter variables except loop counters.
- Load with `<script src="script.js" defer></script>`. Wrap page-specific code in a check like `if (document.querySelector("#rle-demo")) { ... }` so one file works on every page.
- Set text with `textContent`, not `innerHTML`, when the value comes from user input.

## Interactive element (Module 1, element 5)
- Controls are real elements: `<input type="range">`, `<button>`, `<input type="text">`, each with a `<label>`.
- Show results in an element with `aria-live="polite"` so changes are announced.
- Update on the `input` event for sliders (live), on `click` for buttons.

## RLE demo pattern
- `encodeRLE(text)`: walk the string, count repeats, build pairs like `4A3B`.
- `decodeRLE(encoded)`: reverse it. Validate input and show a friendly message on bad input.
- Show original length, encoded length, and the percentage saved, computed with code.
- The explanation of how RLE works is the user's content: leave a CONTENT-TODO.

## Quiz pattern (the questions are the user's content)
- Keep questions as data, separate from logic:
```
// CONTENT-TODO [quiz-q1]: write question, 4 choices, index of correct choice, one-line explanation
const questions = [
  { question: "", choices: ["", "", "", ""], correct: 0, explanation: "" },
];
```
- Logic only: render one question, check the selected choice, keep the score, show the result.
- Skip empty placeholder questions when rendering. Never invent questions or answers.

## Audio
- Prefer the HTML5 `<audio>` element (see semantic-html). If the spec asks for Web Audio, create the `AudioContext` on a user click (browsers block autoplay), and use one `OscillatorNode` + `GainNode`.

## Quick checks
- `node --check script.js` passes
- No `console.error` or unhandled errors on page load
- Every control works with the keyboard (Tab, Enter, arrow keys for sliders)
