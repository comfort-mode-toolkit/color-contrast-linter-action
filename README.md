# Color Contrast Linter Action: Automated Accessibility Testing for CI/CD

[![Accessibility Check](https://github.com/your-username/color-contrast-linter-action/actions/workflows/accessibility.yml/badge.svg)](https://github.com/your-username/color-contrast-linter-action/actions/workflows/accessibility.yml)

**Stop manually copy-pasting hex codes into websites.** Automate your color contrast checking directly in your CI/CD pipeline with the **Color Contrast Linter Action**.

This GitHub Action uses `color-contrast-linter` to check your design tokens and CSS color pairs against WCAG AA and AAA standards, ensuring your application is accessible to everyone.

## The Problem vs. The Solution

### The Old Way (Manual & Error-Prone)
1.  Open your CSS file.
2.  Copy a hex code.
3.  Open a web-based contrast checker.
4.  Paste the hex code.
5.  Repeat for the background color.
6.  *Repeat 50x for every color pair in your app.*
7.  Hope you didn't miss anything.

### The New Way (Automated & Reliable)
1.  Push your code.
2.  **Color Contrast Linter Action** runs automatically in your CI.
3.  Get immediate feedback if any color pair fails WCAG standards.
4.  Merge with confidence.

## Features

-   **Automated CI/CD Integration**: Catch accessibility issues before they reach production.
-   **WCAG Compliance**: Checks against WCAG 2.1 AA and AAA standards.
-   **Easy Configuration**: Define your color pairs once in a simple YAML file.
-   **Detailed Reporting**: See exactly which pairs failed and why.

## Color Tuning

If you need to fix a color pair that fails contrast checks, but you want to keep the new color as visually similar to the original as possible, check out [cm-colors](https://github.com/comfort-mode-toolkit/cm-colors/).

`cm-colors` is a smart color tuning library that can automatically adjust your colors to meet AA or AAA standards while minimizing the visual difference.

## Usage

Add this action to your GitHub Actions workflow (e.g., `.github/workflows/accessibility.yml`):

```yaml
name: Accessibility Check

on: [push, pull_request]

jobs:
  lint-colors:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Check Color Contrast
        uses: your-username/color-contrast-linter-action@main
```

## Configuration

The action looks for a `.color_pairs.yml` file in your repository root. This file defines the color pairs you want to check.

### Generating a Config File
You can generate a starter configuration file locally using the CLI:

```bash
# Install the linter locally
pip install color-contrast-linter

# Generate the config
cc-lint init
```

### Example `.color_pairs.yml`

```yaml
min_contrast: AA
pairs:
  - foreground: "#000000"
    background: "#ffffff"
  - foreground: "#767676"
    background: "#ffffff"
    min_contrast: AAA # Override global setting for this pair
```

## License

[GNU General Public License v3.0](LICENSE)
