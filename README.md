# Textreme
Musings - Primarily Python/HTML/JS

REACT Framework: https://react.dev/
QUILJS Framework: https://quilljs.com/

This version loads all required frameworks from the CDN provider directly. You can use local just fine for completely offline use if downloaded dependencies. Ask your friendly local AI agent to help you get set up.
This has no relation to that other Godot project with apparently the same-ish goals and name. We race towards entropy!
Can then invoke from a static folder from html with : 

- babel.min.js
- quill.min.js
- quill.snow.css
- react-dom.production.min.js
- react.production.min.js

Good luck! 👋

----About / Information----

*** ERROR PRONE — NOT FULLY TESTED, LIKELY NOT OPTIMIZED FOR PERFORMANCE ***

What's broken? Local file operations (load in particular noticed). Some text effects not working as intended but frankly effective enough.

*** THIS IS A (pretty functional despite above issue(s)) BOILERPLATE FOR FUN / IDEAS ***

Features

- Multi-tab workspace — Floating draggable/resizable windows, each containing a Quill editor instance.
- Tabs can be created, renamed, closed, and focus-tracked.
- Quill rich-text editing — Full toolbar with headers, bold/italic/underline/strike, colors, lists, blockquotes, code blocks, links, images.
- Dark / Light theme toggle — CSS variables swap the entire palette, including Quill's toolbar and tooltip styling.
- Character-by-character typing animations (the main "stomping ground").
- Generative effects (on keypress/insert): flyIn, digitize, pop, slam, spin, wave, typewriter, glitch, inkBlot, magnetic, xirtam (Matrix rain).
- Destructive effects (on delete/backspace): destroy, evaporate, suck, debris, blackHole, confetti, shatter, cut.
- Each effect has CSS @keyframes with tunable params via CSS custom properties (--char-anim-duration, --char-s1, --char-dx, etc.).
- Configurable: duration, offset, intensity, direction (for flyIn).
- Row glow — On newline, a glow effect highlights either the previous line or all consecutive non-empty lines above.
- Split pane layout — Windows can be split horizontally or vertically with draggable handles.
- Toolbar controls — Buttons for new tab, theme toggle, animation settings (effect selector, duration slider, intensity slider, delete effect selector).

Architecture

- Single `<script type="text/babel">` block with inline JSX compiled client-side by Babel standalone.
- React hooks (useState, useEffect, useRef, useCallback, useMemo) for all state management.
- Quill instances created imperatively per editor, with custom event listeners hooked into text-change for character animation overlays.
- Overlay `<span>` elements are appended to document.body absolutely positioned at cursor coordinates, animated via CSS, then cleaned up on animationend.
- An EFFECTS registry object maps each effect name to its param generator function.


Current Dependencies (CDN) ✅

| Library | Version | Purpose |
|---|---:|---|
| React | 18.2.0 | UI framework |
| ReactDOM | 18.2.0 | DOM renderer |
| Babel standalone | 7.24.0 | Client-side JSX transpilation |
| Quill | 1.3.7 | Rich-text editor core + snow theme CSS |

Quick Links 🔗

- React: https://react.dev/
- Quill: https://quilljs.com/
- Babel: https://babeljs.io/


Quick Start (static HTML) 🚀

1. Place the following files in the same folder as your HTML (or reference via CDN):
   - `babel.min.js`, `quill.min.js`, `quill.snow.css`, `react-dom.production.min.js`, `react.production.min.js`
2. Include the CSS and scripts in your HTML head/body.
3. Open the HTML file in a browser that supports ES6.

Notes / Troubleshooting 🛠️

- This project compiles JSX client-side via Babel; for production consider a build step to precompile for performance and offline use.
- If local file loading fails, try serving the folder via a simple static server (python -m http.server) instead of opening the file:// URL.
- Some animation effects are experimental — if you see visual glitches, try adjusting CSS custom properties like `--char-anim-duration` or `--char-s1`.

Known Issues / Caveats ⚠️

- Local file operations (load/save) are the most commonly reported failure point.
- Performance may degrade with many open tabs / large documents.
- Accessibility has not been thoroughly audited — use caution for production accessibility requirements.

Contributing & Ideas 💡

- No. 

License & Disclaimer

- Use this project for fun, experimentation, and learning. No warranty — use at your own risk.

Enjoy! ✨
