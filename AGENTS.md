# AGENTS.md - Website Development Guidelines

## Project Overview

This is a personal static website built with plain HTML and CSS. No JavaScript, build tools, frameworks, or package managers are used.

## Directory Structure

```
/home/prokhor/Projects/website/
├── index.html              # Home page (about info)
├── projects/index.html    # Projects page
├── 404.html               # Error page
├── assets/
│   ├── css/
│   │   ├── reset.css      # CSS reset
│   │   └── styles.css     # Main styles
│   ├── cv.pdf             # Resume/CV
│   └── favicon.ico        # Site favicon
├── README.md
└── AGENTS.md
```

## Build/Lint/Test Commands

This is a **static website** - there are no build, lint, or test commands.

- **Development**: Open `index.html` directly in a browser, or serve locally with any static server:
  ```bash
  npx serve .          # Using npx
  python3 -m http.server 8000  # Using Python
  ```
  Note: Use `--prefix /website` flag when serving locally to match deployment paths:
  ```bash
  npx serve . --prefix /website
  ```
- **Deployment**: Deploy to GitHub Pages or any static hosting (Netlify, Vercel, etc.)

## Code Style Guidelines

### HTML

- Use HTML5 doctype: `<!DOCTYPE html>`
- Use 4 spaces for indentation
- Self-closing tags for void elements (e.g., `<meta ...>`, `<link ...>`, `<br>`)
- Attributes use double quotes
- Lowercase tags and attributes
- Include `lang` attribute on `<html>`: `<html lang="en">`
- Include viewport meta tag for responsiveness
- Page titles (in `<title>`) should be empty
- All text content should be lowercase

Example:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title></title>
    <link rel="stylesheet" href="/website/assets/css/styles.css">
</head>
<body>
    <header>
        <nav>
            <a href="/website/">home</a>
            <a href="/website/projects/">projects</a>
        </nav>
    </header>
    <main>
        <ul>
            <li>email: <a href="mailto:example@example.com">example@example.com</a></li>
        </ul>
    </main>
    <footer>
        &copy; 2026
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

### Naming Conventions

- **Files**: lowercase with hyphens (e.g., `styles.css`)
- **CSS classes**: lowercase with hyphens (e.g., `.cat-art`, `.timestamp`)
- **HTML ids**: lowercase with hyphens

### Paths

- Use absolute paths starting with `/website/` for assets (e.g., `/website/assets/css/styles.css`)
- Links within the site should follow the same pattern (e.g., `/website/projects/`)

### Page Structure

- All pages should have: header with cat art, nav, main content, footer
- Nav should include "home" and "projects" links on all pages
- No page titles (h1) should be displayed - use empty `<title>` tags
- All text should be lowercase
- Footer should show `&copy; 2026`

### Accessibility

- Use semantic HTML elements (`<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`)
- Include `alt` text for images
- Use meaningful link text (avoid "click here")
- Ensure sufficient color contrast (current: light text on dark background)

## Common Tasks

### Adding a new project
1. Edit `projects/index.html`
2. Add a new `<div class="project">` with `<h2>` (project title/link) and `<p>` (description)

### Adding a new CSS rule
1. Edit `assets/css/styles.css`
2. Follow existing formatting (4 spaces, one property per line)
3. Group with related rules

## Notes for Agents

- This is a personal website - keep changes minimal and consistent with existing style
- Do not add JavaScript, frameworks, build tools, or testing frameworks
- Do not add TypeScript or CSS preprocessors
- Maintain the dark theme aesthetic (#191919 background, #d9d9d9 text)
- Keep the cat ASCII art in the header
- The site uses monospace fonts throughout
- Do not add page titles (h1) to pages
- All text content should be lowercase
