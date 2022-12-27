---
title: Vite-tailwind
layout: home
---

## <ins>Getting Started</ins>

### Overview

Vite (French word for "quick", pronounced /vit/, like "veet") is a build tool that aims to provide a faster and leaner development experience for modern web projects. It consists of two major parts:

* A dev server that provides rich feature enhancements over native ES modules, for example extremely fast Hot Module Replacement (HMR).

* A build command that bundles your code with Rollup, pre-configured to output highly optimized static assets for production.

Vite is opinionated and comes with sensible defaults out of the box, but is also highly extensible via its Plugin API and JavaScript API with full typing support.

### How to install

```bash
    npm create vite@latest
```

Then follow the prompt!

You can also directly specify the project name and the template you want to use via additional command line options. For example, to scaffold a Vite + React project, run:

```bash
npm create vite@latest my-vite-app --template react
```

Then

```bash
cd ./my-vite-app
```

follow by

```bash
npm install
```

### Install tailwind

```bash
npm install -D tailwindcss postcss autoprefixer
```

```bash
npx tailwindcss init -p
```

Add the paths to all of your template files in your tailwind.config.js file.

```bash
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Add the @tailwind directives for each of Tailwind’s layers to your ./src/index.css file.

```bash
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### All configs done. Y can now start the project with

```bash
npm run dev
```
