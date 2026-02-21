# AGENTS.md - Website Development Guidelines

## Project Overview

This is a personal static website built with plain HTML, CSS, and JavaScript. No build tools, frameworks, or package managers are used.

## Directory Structure

```
/home/prokhor/Projects/website/
├── index.html              # Home page
├── about/index.html       # About page
├── thoughts/index.html    # Thoughts/blog page
├── projects/index.html    # Projects page
├── 404.html               # Error page
├── assets/
│   ├── css/
│   │   ├── reset.css      # CSS reset
│   │   └── styles.css     # Main styles
│   ├── js/
│   │   └── quote.js       # Random quote widget
│   ├── cv.pdf             # Resume/CV
│   └── favicon.ico        # Site favicon
└── README.md
```

## Build/Lint/Test Commands

This is a **static website** - there are no build, lint, or test commands.

- **Development**: Open `index.html` directly in a browser, or serve locally with any static server:
  ```bash
  npx serve .          # Using npx
  python3 -m http.server 8000  # Using Python
  ```
- **Deployment**: Deploy the `assets/` folder and HTML files to any static hosting (GitHub Pages, Netlify, Vercel, etc.)

## Code Style Guidelines

### HTML

- Use HTML5 doctype: `<!DOCTYPE html>`
- Use 4 spaces for indentation
- Self-closing tags for void elements (e.g., `<meta ...>`, `<link ...>`, `<br>`)
- Attributes use double quotes
- Lowercase tags and attributes
- Include `lang` attribute on `<html>`: `<html lang="en">`
- Include viewport meta tag for responsiveness

Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
    <link rel="stylesheet" href="/website/assets/css/styles.css">
</head>
<body>
    <header>
        <nav>
            <a href="/website/">home</a>
            <a href="/website/thoughts/">thoughts</a>
        </nav>
    </header>
    <main>
        <p>Content here</p>
    </main>
    <footer>
        &copy; 2025
    </footer>
</body>
</html>
```

### CSS

- Use 4 spaces for indentation
- One property per line
- Use meaningful class names (lowercase, hyphenated)
- Group related properties (positioning, box model, typography, visual)
- Use CSS variables for colors if needed
- Prefer flexbox for layout
- Use monospace font as default (see existing styles.css)

Example:
```css
body {
    font-family: monospace;
    max-width: 450px;
    margin: 0 auto;
    padding: 20px;
    line-height: 1.5;
    color: #d9d9d9;
    background-color: #191919;
}

a {
    color: #d9d9d9;
    text-decoration: none;
    border-bottom: 1px dotted #d9d9d9;
}

a:hover {
    border-bottom: 1px solid #d9d9d9;
}
```

### JavaScript

- Use `const` for constants and arrays, `let` for mutable variables
- Use `function` declarations (not arrow functions for top-level functions)
- Use double quotes for strings
- Use 4 spaces for indentation
- Declare functions before they are used (no hoisting依赖)
- Use meaningful variable and function names (camelCase)
- Keep functions focused and small

Example:
```javascript
const quotes = [
    {
        "quote": "Sample quote.",
        "author": "Author Name",
        "profession": "Profession",
        "topics": ["Topic1", "Topic2"]
    }
];

function displayRandomQuote() {
    const randomIndex = Math.floor(Math.random() * quotes.length);
    const randomQuote = quotes[randomIndex];

    document.getElementById('quote-text').textContent = `"${randomQuote.quote}"`;
    document.getElementById('quote-author').textContent = `— ${randomQuote.author}`;
}

displayRandomQuote();
```

### Naming Conventions

- **Files**: lowercase with hyphens (e.g., `quote-widget.js`, `styles.css`)
- **CSS classes**: lowercase with hyphens (e.g., `.cat-art`, `.timestamp`)
- **JavaScript variables/functions**: camelCase (e.g., `displayRandomQuote`, `randomIndex`)
- **HTML ids**: lowercase with hyphens (e.g., `quote-text`, `quote-author`)

### Paths

- Use absolute paths starting with `/website/` for assets (e.g., `/website/assets/css/styles.css`)
- Links within the site should follow the same pattern (e.g., `/website/thoughts/`)

### Error Handling

- For simple static JS, use basic DOM checks (e.g., `document.getElementById('element')`)
- No error boundaries or try/catch needed for this simple site
- Ensure elements exist before manipulating them

### Accessibility

- Use semantic HTML elements (`<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`)
- Include `alt` text for images
- Use meaningful link text (avoid "click here")
- Ensure sufficient color contrast (current: light text on dark background)

## Common Tasks

### Adding a new page
1. Create new HTML file in appropriate directory
2. Copy structure from existing page (index.html)
3. Update title, navigation, and content
4. Add corresponding nav link to all pages

### Adding a new CSS rule
1. Edit `assets/css/styles.css`
2. Follow existing formatting (4 spaces, one property per line)
3. Group with related rules

### Adding new quotes
1. Edit `assets/js/quote.js`
2. Add new object to `quotes` array following existing format
3. Ensure all fields are present: quote, author, profession, topics

### Modifying the quote widget
- The widget displays a random quote on page load
- HTML elements required: `#quote-text`, `#quote-author`, optionally `#quote-profession`, `#quote-topics`
- Function `displayRandomQuote()` handles the display logic

## Notes for Agents

- This is a personal website - keep changes minimal and consistent with existing style
- Do not add JavaScript frameworks, build tools, or testing frameworks
- Do not add TypeScript or CSS preprocessors
- Maintain the dark theme aesthetic (#191919 background, #d9d9d9 text)
- Keep the cat ASCII art in the header
- The site uses monospace fonts throughout
