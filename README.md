# Color Contrast Linter Action

A GitHub Action to lint color pairs for accessibility contrast compliance using `color-contrast-linter`.

## Usage

Create a workflow file (e.g., `.github/workflows/accessibility.yml`):

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

Ensure you have a `.color_pairs.yml` file in your repository root. You can generate one locally using:

```bash
cc-lint init
```

Example `.color_pairs.yml`:

```yaml
min_contrast: AA
pairs:
  - foreground: "#000000"
    background: "#ffffff"
```
