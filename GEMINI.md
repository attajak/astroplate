# AstroPlate Project Guide

## Project Overview

**AstroPlate** is a boilerplate project built with **Astro**, **React**, and **TailwindCSS**. It provides a solid foundation for building static sites with a focus on performance and ease of customization.

**Key Technologies:**
*   **Astro:** v5.x (Static Site Generator)
*   **React:** v19.x (UI Framework)
*   **TailwindCSS:** v4.x (Utility-first CSS)
*   **TypeScript:** Type safety
*   **MDX:** Content authoring with components

## Directory Structure

*   **`src/content/`**: Contains the site's content in MDX format (blog posts, authors, pages, etc.). Defined in `src/content.config.ts`.
*   **`src/layouts/`**: Astro layouts, components, and shortcodes.
    *   `components/`: Reusable UI components.
    *   `partials/`: Page sections like Header, Footer.
    *   `shortcodes/`: Components usable within MDX files.
*   **`src/pages/`**: File-based routing for the application.
*   **`src/styles/`**: CSS files.
    *   `main.css`: The entry point for styles.
    *   `generated-theme.css`: **Do not edit manually.** Generated from `src/config/theme.json`.
*   **`src/config/`**: Configuration files.
    *   `config.json`: General site settings (title, URL, toggleable features).
    *   `theme.json`: Theme design system (colors, fonts).
    *   `menu.json`: Navigation menu structure.
*   **`scripts/`**: Node.js scripts for build tasks.
    *   `themeGenerator.js`: Generates CSS variables from `theme.json`.
    *   `jsonGenerator.js`: Generates JSON data for search/API.

## Configuration

### Site Settings
Located in **`src/config/config.json`**. Controls:
*   Site title, logo, and favicon.
*   Feature toggles (search, dark mode, etc.).
*   Third-party integrations (Google Tag Manager, Disqus).

### Theme Customization
Located in **`src/config/theme.json`**. Controls:
*   **Colors:** Default and Dark mode palettes.
*   **Fonts:** Font families and base sizes.
*   **Note:** The `scripts/themeGenerator.js` script must run to apply changes made here (happens automatically in `dev` and `build`).

### Astro Configuration
Located in **`astro.config.mjs`**. Configures integrations (React, MDX, Sitemap, TailwindCSS) and markdown plugins.

## Building and Running

The project uses `yarn` (v1.22.22) as the package manager, but `npm` commands usually work via the `scripts` definition.

| Command | Description |
| :--- | :--- |
| `npm run dev` | Starts the development server. Runs theme generator and JSON generator in parallel. |
| `npm run build` | Builds the project for production. |
| `npm run preview` | Previews the built project locally. |
| `npm run format` | Formats code using Prettier. |
| `npm run check` | Runs `astro check` for type checking. |

## Development Conventions

*   **Path Aliases:** Use the configured aliases for cleaner imports:
    *   `@/components/*` -> `src/layouts/components/*`
    *   `@/shortcodes/*` -> `src/layouts/shortcodes/*`
    *   `@/partials/*` -> `src/layouts/partials/*`
    *   `@/helpers/*` -> `src/layouts/helpers/*`
*   **Styling:**
    *   Use Tailwind utility classes for most styling.
    *   Use CSS variables (e.g., `--color-primary`) generated from `theme.json` for consistent theming.
    *   `src/styles/main.css` uses Tailwind v4 `@theme` and `@plugin` directives.
*   **Content:**
    *   Create new content in `src/content/`.
    *   Follow the schema defined in `src/content.config.ts`.
