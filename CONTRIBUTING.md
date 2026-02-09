# Contributing to Power BI Themes Library

Thank you for your interest in contributing! This document provides guidelines for contributing themes, snippets, and improvements to this library.

---

## 🎯 Ways to Contribute

1. **New Themes** — Submit complete theme files
2. **Visual Snippets** — Add visual-specific configurations
3. **Documentation** — Improve guides and examples
4. **Bug Reports** — Report issues with existing themes
5. **Feature Requests** — Suggest new features or improvements

---

## 📋 Theme Submission Guidelines

### Quality Standards

All submitted themes must meet these requirements:

#### 1. Accessibility
- **Contrast ratio:** Minimum WCAG 2.1 AA (4.5:1 for normal text)
- **Color blindness:** Test with color blindness simulators
- **Readability:** Text must be readable at default sizes

#### 2. Completeness
- Include all required theme properties
- Set meaningful values (not just defaults)
- Document color choices and rationale

#### 3. Testing
- Test with multiple visual types (bar, line, table, card, slicer)
- Test on both desktop and mobile layouts
- Verify tooltips, labels, and legends

#### 4. Naming
- **File naming:** `lowercase_with_underscores.json`
- **Theme name:** Descriptive and professional
- **Example:** `corporate_blue_professional.json`

---

## 🚀 Submission Process

### 1. Fork the Repository

```bash
git clone https://github.com/Rakcheyev/powerbi-themes.git
cd powerbi-themes
git checkout -b feature/new-theme-name
```

### 2. Add Your Theme

**For complete themes:**
```bash
# Add theme file
cp your-theme.json themes/your-theme.json

# Test in Power BI Desktop
# View → Themes → Browse → Select your-theme.json
```

**For visual snippets:**
```bash
# Add snippet file
cp your-visual-snippet.json snippets/your-visual-snippet.json
```

### 3. Update Documentation

Add your theme to README.md:

```markdown
| **your_theme.json** | Brief description | Best for: Use cases |
```

### 4. Create Pull Request

```bash
git add .
git commit -m "feat: add [theme name] theme

- Description of theme
- Color palette used
- Target use cases
- Testing completed"

git push origin feature/new-theme-name
```

Then open a pull request on GitHub.

---

## 📝 Theme Template

Use this structure for new themes:

```json
{
  "name": "Your Theme Name",
  "dataColors": [
    "#color1",
    "#color2",
    "#color3",
    "#color4",
    "#color5",
    "#color6",
    "#color7",
    "#color8"
  ],
  "background": "#ffffff",
  "foreground": "#252423",
  "tableAccent": "#118dff",
  "good": "#00b050",
  "neutral": "#ffc000",
  "bad": "#ff0000",
  "maximum": "#0078d7",
  "center": "#ffc000",
  "minimum": "#ff0000",
  "null": "#bfbfbf",
  "visualStyles": {
    "*": {
      "*": {
        "background": [{"color": {"solid": {"color": "#ffffff"}}}],
        "general": [{"responsive": true}],
        "title": [
          {"fontColor": {"solid": {"color": "#252423"}}},
          {"fontSize": 12},
          {"fontFamily": "Segoe UI"}
        ]
      }
    }
  }
}
```

---

## 🎨 Color Palette Guidelines

### Data Colors Array

- **Minimum:** 8 colors (required by Power BI)
- **Recommended:** 8-12 colors for variety
- **Distinctiveness:** Colors should be easily distinguishable
- **Harmony:** Use a coherent color scheme (analogous, complementary, triadic)

### Semantic Colors

| Property | Purpose | Guidelines |
|----------|---------|-----------|
| `good` | Positive values, success | Green tones (#00b050) |
| `neutral` | Neutral values, warnings | Orange/yellow tones (#ffc000) |
| `bad` | Negative values, errors | Red tones (#ff0000) |
| `maximum` | Highest values | Blue tones (#0078d7) |
| `minimum` | Lowest values | Red tones (#ff0000) |

---

## 🧪 Testing Checklist

Before submitting, verify your theme works correctly:

### Visual Types
- [ ] Bar/Column charts
- [ ] Line/Area charts
- [ ] Pie/Donut charts
- [ ] Cards and KPIs
- [ ] Tables and Matrices
- [ ] Slicers (dropdown, list, date)
- [ ] Maps
- [ ] Scatter/Bubble charts
- [ ] Funnel/Waterfall charts
- [ ] Gauges

### Elements
- [ ] Chart titles
- [ ] Axis labels
- [ ] Data labels
- [ ] Legends
- [ ] Tooltips
- [ ] Grid lines
- [ ] Backgrounds
- [ ] Borders

### Scenarios
- [ ] Single visual
- [ ] Multiple visuals on page
- [ ] Drill-down/drill-through
- [ ] Conditional formatting
- [ ] Light/dark mode (if applicable)

---

## 📖 Documentation Standards

When adding themes, include:

1. **Description:** What is this theme for?
2. **Color palette:** List primary colors used
3. **Use cases:** When to use this theme
4. **Accessibility notes:** WCAG compliance level
5. **Examples:** Screenshots (optional but recommended)

---

## 🐛 Reporting Issues

When reporting issues with existing themes:

1. **Theme name:** Which theme has the issue?
2. **Power BI version:** Desktop version number
3. **Visual type:** Which visual is affected?
4. **Expected behavior:** What should happen?
5. **Actual behavior:** What actually happens?
6. **Screenshots:** If applicable

---

## 💡 Feature Requests

We welcome suggestions for:

- New theme concepts
- Additional visual snippets
- Documentation improvements
- Tooling enhancements (validators, preview generators, etc.)

---

## 📜 Code of Conduct

- Be respectful and constructive
- Provide clear, helpful feedback
- Credit original sources when applicable
- Follow theme naming and structure conventions

---

## ⚖️ License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

## 🙏 Thank You!

Your contributions help make Power BI development more consistent, accessible, and efficient for everyone!

---

**Questions?** Open an issue or discussion on GitHub.
