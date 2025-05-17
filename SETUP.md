# ExamSeasonTemplate Setup Guide

This document provides a comprehensive guide for setting up and using the ExamSeasonTemplate with React, Vite, and Tailwind CSS v4.

## Table of Contents

- [What's Included](#whats-included)
- [Getting Started](#getting-started)
- [Important Tailwind CSS v4 Changes](#important-tailwind-css-v4-changes)
- [Deployment](#deployment)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)

## What's Included

This template comes pre-configured with:

- **React 19** - The latest version of React
- **Vite** - Fast build tool and development server
- **Tailwind CSS v4** - Utility-first CSS framework with simplified setup
- **ESLint** - Code linting
- **GitHub Actions** - Automatic deployment to GitHub Pages
- **Responsive Components** - Header, Hero, Features, and Footer

## Getting Started

### Using This Template

1. **Clone the repository**

```bash
git clone https://github.com/RobertsLuke/ExamSeasonTemplate.git your-project-name
cd your-project-name
```

2. **Update Git remote**

```bash
git remote remove origin
git remote add origin https://github.com/yourusername/your-project-name.git
```

3. **Install dependencies**

```bash
npm install
```

4. **Start the development server**

```bash
npm run dev
```

5. **Update project details**
   - Update `package.json` with your project name, version, and description
   - Update `vite.config.js` to change the base path if necessary
   - Update `README.md` to reflect your project
   - Update the title in `index.html`

### Creating a New Project From Scratch

If you prefer to create a new project with similar setup:

1. **Create a Vite project**

```bash
npm create vite@latest my-project -- --template react
cd my-project
```

2. **Install Tailwind CSS v4 and Vite plugin**

```bash
npm install tailwindcss @tailwindcss/vite
```

3. **Configure Vite for Tailwind CSS v4**

```javascript
// vite.config.js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react-swc'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [react(), tailwindcss()],
})
```

4. **Set up CSS with Tailwind import**

```css
/* src/index.css */
@import "tailwindcss";

/* Your custom styles below */
```

5. **Import CSS in your main file**

```javascript
// src/main.jsx
import './index.css'
// Rest of your code
```

## Important Tailwind CSS v4 Changes

Tailwind CSS v4 introduces several key changes compared to v3:

### 1. Simplified Import

Instead of the previous directives:
```css
/* Old way (v3) */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

You now use a single import:
```css
/* New way (v4) */
@import "tailwindcss";
```

### 2. No Configuration File Required

Tailwind CSS v4 doesn't require a `tailwind.config.js` file for basic usage. It automatically detects template files.

### 3. Vite Plugin

Use the official `@tailwindcss/vite` plugin instead of PostCSS configuration:

```javascript
// vite.config.js
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    // other plugins,
    tailwindcss()
  ],
})
```

### 4. OKLCH Color System

Tailwind v4 uses the OKLCH color system for more vibrant colors. This is handled automatically.

### 5. Custom Styling

If you need custom styling, use the CSS file where you import Tailwind:

```css
@import "tailwindcss";

/* Custom theme */
:root {
  --primary-color: oklch(0.7 0.28 145);
}

/* Custom styles */
.my-component {
  /* styles here */
}
```

## Deployment

### GitHub Pages

This template is pre-configured for GitHub Pages deployment:

1. **Enable GitHub Pages**:
   - Go to your repository's Settings > Pages
   - Under "Build and deployment", select "GitHub Actions"

2. **Update the base path**:
   - In `vite.config.js`, ensure the base path matches your repository name:
   ```javascript
   export default defineConfig({
     // other config
     base: '/your-repository-name/',
   })
   ```

3. **Push to main branch**:
   - The GitHub Action will automatically build and deploy your site

4. **Access your site**:
   - Your site will be available at `https://yourusername.github.io/your-repository-name/`

### Other Hosting Platforms

To deploy to other platforms:

1. **Build your project**:
   ```bash
   npm run build
   ```

2. **Deploy the `dist` folder**:
   - The built project will be in the `dist` directory
   - Upload this to your hosting provider

## Best Practices

### Project Structure

Keep your project organized:

```
your-project/
├── public/               # Static assets
├── src/
│   ├── components/       # Reusable UI components
│   ├── pages/            # Page components
│   ├── hooks/            # Custom React hooks
│   ├── utils/            # Utility functions
│   ├── contexts/         # React contexts
│   ├── assets/           # Images, fonts, etc.
│   ├── App.jsx           # Main application component
│   ├── index.css         # Global styles and Tailwind import
│   └── main.jsx          # Application entry point
├── .github/workflows/    # GitHub Actions workflows
├── index.html            # HTML template
├── vite.config.js        # Vite configuration
└── package.json          # Project dependencies and scripts
```

### Tailwind Best Practices

1. **Use Utility Classes First**:
   - Embrace Tailwind's utility-first approach
   - Only create custom components when necessary

2. **Mobile-First Design**:
   - Start with mobile designs
   - Use responsive modifiers (`sm:`, `md:`, `lg:`, etc.) for larger screens

3. **Keep Utilities Together**:
   - Group related utilities for better readability
   ```html
   <!-- Position utilities -->
   <div class="absolute top-0 right-0
               <!-- Size utilities -->
               w-full h-16
               <!-- Visual utilities -->
               bg-white shadow-md">
   ```

4. **Extract Components When Needed**:
   - Identify repeated patterns
   - Create reusable React components

## Troubleshooting

### Common Issues

1. **Styles Not Applying**:
   - Ensure you've imported the CSS file in your main file
   - Check that your HTML elements have the correct class names

2. **GitHub Pages Deployment Fails**:
   - Verify that GitHub Pages is enabled in repository settings
   - Ensure the base path in `vite.config.js` matches your repository name
   - Check that the GitHub Action has the proper permissions

3. **Development Server Issues**:
   - Clear your browser cache
   - Restart the development server
   - Check for error messages in the terminal

4. **Dependencies Conflicts**:
   - Make sure all packages are compatible
   - Update packages to their latest versions
   ```bash
   npm update
   ```

### Contact

If you encounter any issues or have questions about this template, please open an issue on the [GitHub repository](https://github.com/RobertsLuke/ExamSeasonTemplate).

---

Happy coding! 🚀