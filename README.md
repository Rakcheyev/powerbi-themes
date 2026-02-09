# Power BI Themes Library

> **Reusable theme library for Power BI reports**
>
> A curated collection of professional Power BI themes, visual-specific snippets, and templates for creating consistent, accessible, and beautiful Power BI reports.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop%202025%2B-yellow)](https://powerbi.microsoft.com/)

---

## 📦 What's Included

- **6 Production Themes** — Ready-to-use complete theme files
- **13 Visual Snippets** — Visual-specific configurations
- **Complete Template** — Full reference template with all properties
- **Documentation** — Comprehensive theme properties reference

---

## 🚀 Quick Start

### Installation

**Option 1: Git Submodule (Recommended for projects)**
```bash
cd your-powerbi-project
git submodule add https://github.com/Rakcheyev/powerbi-themes.git themes
git submodule update --init
```

**Option 2: Direct Clone**
```bash
cd your-powerbi-project
git clone https://github.com/Rakcheyev/powerbi-themes.git themes
```

**Option 3: Manual Download**
- Download specific theme files as needed
- No git integration required

### Applying a Theme

1. Open Power BI Desktop
2. Go to **View** → **Themes** → **Browse for themes**
3. Navigate to `themes/` folder
4. Select a theme JSON file
5. Click **Open**

---

## 🎨 Available Themes

### Production Themes

| Theme | Description | Best For |
|-------|-------------|----------|
| **corporate_dark_purple.json** | Professional dark theme with purple accents | Corporate dashboards, executive reports |
| **dark_modern.json** | Modern dark theme | Data-heavy reports, analytics dashboards |
| **foxtrot_warm.json** | Warm color palette | Marketing reports, customer-facing dashboards |
| **high_contrast_accessible.json** | WCAG 2.1 AA compliant | Accessibility-first reports |
| **lavender_professional.json** | Professional light theme with lavender | General business reports |
| **light_professional.json** | Clean professional light theme | Standard business reports |

### Preview

*(Add screenshots here if desired)*

---

## 🧩 Visual Snippets

The `snippets/` folder contains visual-specific configurations you can merge into your themes:

- `barChart.json` — Bar/column chart styling
- `card.json` — Card visual styling
- `donutChart.json` — Donut/pie chart styling
- `funnelChart.json` — Funnel chart styling
- `gauge.json` — Gauge visual styling
- `kpi.json` — KPI visual styling
- `lineChart.json` — Line/area chart styling
- `maps.json` — Map visual styling
- `scatterChart.json` — Scatter chart styling
- `slicer.json` — Slicer styling
- `tableMatrix.json` — Table/matrix styling
- `waterfallChart.json` — Waterfall chart styling

### Using Snippets

Copy properties from snippet files into your theme's `visualStyles` section to customize specific visuals.

---

## 📚 Templates

### Complete Theme Template

`templates/complete_theme_template.json` contains all available theme properties with default values and comments.

Use this as a starting point for creating custom themes.

---

## 📖 Documentation

- **[Theme Properties Reference](themes/docs/PowerBI_Theme_Properties_Complete_Reference.md)** — Complete documentation of all theme properties
- **[Creating Custom Themes](examples/)** — Examples and guides

---

## 🛠️ Creating Custom Themes

1. **Start with a template:**
   ```bash
   cp templates/complete_theme_template.json my-custom-theme.json
   ```

2. **Edit properties:**
   - Modify colors in the `dataColors` array
   - Update `foreground`, `background` for base colors
   - Customize visual styles as needed

3. **Test in Power BI Desktop:**
   - Apply theme via View → Themes
   - Check all visual types
   - Verify contrast and accessibility

4. **Share back:**
   - See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Ways to contribute:**
- Submit new themes
- Improve existing themes
- Add visual snippets
- Enhance documentation
- Report issues

---

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

---

## 🔗 Integration

### Power BI Projects

This library is designed to work seamlessly with Power BI projects using PBIP (Power BI Project) format.

**Example integration:**
```bash
your-pbi-project/
├── reports/
│   └── sales-dashboard/
│       ├── pbip/
│       └── ...
└── themes/                 # ← This repository as submodule
    ├── themes/
    ├── snippets/
    └── templates/
```

### Updating Themes

**If using submodule:**
```bash
cd themes
git pull origin main
cd ..
git add themes
git commit -m "chore: update themes library"
```

**If using direct clone:**
```bash
cd themes
git pull origin main
```

---

## 🌟 Examples

See `examples/` folder for real-world theme implementations and usage patterns.

---

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/Rakcheyev/powerbi-themes/issues)
- **Documentation:** [themes/docs/](themes/docs/)

---

## ✨ Acknowledgments

Created to support professional Power BI development with consistent, accessible, and maintainable themes.

---

**Version:** 1.0.0
**Last Updated:** 2026-02-09
