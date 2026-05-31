# Simplest Loader

> A minimal full-screen CSS spinner that covers the page on load and disappears automatically when the content is ready — all in a single HTML file.

---

## Overview

A dead-simple page preloader built with pure CSS and a single JS event listener. A full-screen white overlay with a spinning border circle sits at `z-index: 9999` and gets hidden the moment `window.load` fires. Drop it into any project in seconds.

---

## How It Works

1. A `.loading-animation` div covers the entire viewport on page load
2. A CSS `@keyframes spin` animation rotates a bordered circle infinitely
3. When all assets finish loading, `window.addEventListener('load', ...)` adds the `.hidden` class to dismiss the overlay

---

## Usage

Copy the loader div, style block, and script into your own HTML:

```html
<!-- In <head> -->
<style>
  .loading-animation {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background-color: #fff;
    z-index: 9999;
  }
  .loading-animation::after {
    content: '';
    display: block;
    position: absolute;
    top: 50%; left: 50%;
    width: 60px; height: 60px;
    margin: -30px 0 0 -30px;
    border-radius: 50%;
    border: 6px solid #333;
    border-top-color: #fff;
    animation: spin 3s linear infinite;
  }
  @keyframes spin {
    0%   { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
  .hidden { display: none; }
</style>

<!-- In <body> -->
<div class="loading-animation"></div>

<script>
  window.addEventListener('load', function() {
    document.querySelector('.loading-animation').classList.add('hidden');
  });
</script>
```

---

## Customization

| Property | Default | What it does |
|----------|---------|--------------|
| `background-color` | `#fff` | Overlay background color |
| `border` color | `#333` | Spinner ring color |
| `border-top-color` | `#fff` | Spinner gap color (match background) |
| `width` / `height` | `60px` | Spinner size |
| `animation` duration | `3s` | Spin speed |

---

## Project Structure

```
simplest_loader/
└── load.html   # Self-contained loader demo — markup, styles, and script in one file
```

---

## License

© 2026 Sheikh Muhammad Talha Bin Khalid. All Rights Reserved.
