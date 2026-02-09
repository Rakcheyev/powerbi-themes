# Power BI Theme JSON - Complete Visual Properties Reference Guide

## Table of Contents
1. [Theme JSON Structure Overview](#1-theme-json-structure-overview)
2. [Top-Level Properties](#2-top-level-properties)
3. [Text Classes (textClasses)](#3-text-classes-textclasses)
4. [Visual Styles (visualStyles)](#4-visual-styles-visualstyles)
5. [Common Property Cards](#5-common-property-cards)
6. [Chart-Specific Properties](#6-chart-specific-properties)
7. [Table and Matrix Properties](#7-table-and-matrix-properties)
8. [Slicer Properties](#8-slicer-properties)
9. [Card and KPI Properties](#9-card-and-kpi-properties)
10. [Page and Shape Properties](#10-page-and-shape-properties)
11. [Visual Header and Tooltip](#11-visual-header-and-tooltip)
12. [Filter Pane Properties](#12-filter-pane-properties)
13. [Style Presets](#13-style-presets)
14. [Color Format Reference](#14-color-format-reference)
15. [Complete Example Theme](#15-complete-example-theme)
16. [Resources](#16-resources)

---

## 1. Theme JSON Structure Overview

A Power BI theme JSON file controls the visual appearance of reports. It defines colors, typography, borders, shadows, and individual visual customizations.

### Basic Structure
```json
{
  "name": "Theme Name",
  "dataColors": ["#color1", "#color2"],
  "background": "#FFFFFF",
  "foreground": "#000000",
  "tableAccent": "#118DFF",
  "textClasses": { ... },
  "visualStyles": { ... }
}
```

---

## 2. Top-Level Properties

### 2.1 Required Properties

| Property | Type | Description |
|----------|------|-------------|
| `name` | string | **Required.** Theme name identifier |

### 2.2 Data Color Properties

| Property | Type | Description |
|----------|------|-------------|
| `dataColors` | array | Hex colors for data shapes. Cycles when exhausted |
| `good` | hex string | Status color for positive (KPI, Waterfall) |
| `neutral` | hex string | Status color for neutral values |
| `bad` | hex string | Status color for negative values |
| `maximum` | hex string | Maximum gradient (conditional formatting) |
| `center` | hex string | Center gradient (conditional formatting) |
| `minimum` | hex string | Minimum gradient (conditional formatting) |
| `null` | hex string | Null value color (conditional formatting) |

### 2.3 Structural Color Properties

| Property | Description |
|----------|-------------|
| `firstLevelElements` | Primary foreground (main text, labels) |
| `secondLevelElements` | Secondary text (subtitles, descriptions) |
| `thirdLevelElements` | Gridlines and accents |
| `fourthLevelElements` | Dimmed/disabled colors |
| `background` | Primary background color |
| `secondaryBackground` | Secondary background |
| `foreground` | Foreground color (text, KPI, Card values) |
| `foregroundNeutralSecondary` | Secondary neutral foreground |
| `foregroundNeutralTertiary` | Tertiary neutral foreground |
| `backgroundLight` | Light background |
| `backgroundNeutral` | Neutral background |
| `tableAccent` | Table/matrix accent color |

---

## 3. Text Classes (textClasses)

Text classes define reusable typography styles. There are 4 primary classes; secondary classes inherit automatically.

### 3.1 Primary Text Classes

| Class | Usage | Applies To |
|-------|-------|------------|
| `label` | General text, values | Table/matrix values, axis labels, legends |
| `title` | Titles and headers | Axis titles, chart titles |
| `callout` | Large display text | Card data labels, KPI indicators |
| `header` | Section headers | Key influencer headers, tab headers |

### 3.2 Secondary Text Classes (Auto-inherited)

| Class | Inherits From | Modification |
|-------|---------------|--------------|
| `boldLabel` | label | Bold formatting |
| `smallLabel` | label | Smaller font |
| `largeLabel` | label | Larger font |
| `lightLabel` | label | Lighter color |
| `largeLightLabel` | label | Larger, lighter |
| `smallLightLabel` | label | Smaller, lighter |
| `largeTitle` | title | Larger title |
| `semiboldLabel` | label | Semibold weight |

### 3.3 Text Class Properties

| Property | Type | Description |
|----------|------|-------------|
| `fontSize` | number | Font size in points |
| `fontFace` | string | Font family name |
| `fontFamily` | string | Alternative font family property |
| `color` | hex string | Text color |

**Example:**
```json
"textClasses": {
  "callout": {
    "fontSize": 45,
    "fontFace": "Segoe UI",
    "color": "#252423"
  },
  "title": {
    "fontSize": 12,
    "fontFace": "Segoe UI",
    "color": "#252423"
  },
  "header": {
    "fontSize": 12,
    "fontFace": "Segoe UI Semibold",
    "color": "#252423"
  },
  "label": {
    "fontSize": 10,
    "fontFace": "Segoe UI",
    "color": "#252423"
  }
}
```

---

## 4. Visual Styles (visualStyles)

### 4.1 Structure

```json
"visualStyles": {
  "*": {                    // All visuals (global)
    "*": {                  // All style presets
      "*": [{...}]          // All property cards
    }
  },
  "barChart": {             // Specific visual
    "*": {
      "legend": [{...}],
      "categoryAxis": [{...}]
    }
  }
}
```

### 4.2 Visual Type Names

| JSON Name | Display Name |
|-----------|--------------|
| `barChart` | Clustered Bar Chart |
| `columnChart` | Clustered/Stacked Column Chart |
| `clusteredBarChart` | Clustered Bar Chart |
| `clusteredColumnChart` | Clustered Column Chart |
| `hundredPercentStackedBarChart` | 100% Stacked Bar |
| `hundredPercentStackedColumnChart` | 100% Stacked Column |
| `lineChart` | Line Chart |
| `areaChart` | Area Chart / Stacked Area |
| `lineClusteredColumnComboChart` | Line and Clustered Column |
| `lineStackedColumnComboChart` | Line and Stacked Column |
| `ribbonChart` | Ribbon Chart |
| `waterfallChart` | Waterfall Chart |
| `scatterChart` | Scatter Chart |
| `pieChart` | Pie Chart |
| `donutChart` | Donut Chart |
| `treemap` | Treemap |
| `funnel` | Funnel Chart |
| `gauge` | Gauge |
| `card` | Card |
| `cardVisual` | New Card Visual |
| `multiRowCard` | Multi-row Card |
| `kpi` | KPI |
| `slicer` | Slicer |
| `advancedSlicerVisual` | New Slicer Visual |
| `tableEx` | Table |
| `pivotTable` | Matrix |
| `map` | Map (Bing) |
| `filledMap` | Filled Map |
| `shapeMap` | Shape Map |
| `azureMap` | Azure Map |
| `esriMap` | ArcGIS Map |
| `decompositionTreeVisual` | Decomposition Tree |
| `keyDriversVisual` | Key Influencers |
| `qnaVisual` | Q&A Visual |
| `shape` | Shape |
| `image` | Image |
| `textbox` | Text Box |
| `actionButton` | Button |
| `page` | Report Page Settings |
| `group` | Visual Container Groups |

---

## 5. Common Property Cards

### 5.1 General Properties

| Property | Type | Description |
|----------|------|-------------|
| `responsive` | boolean | Enable responsive sizing |
| `keepLayerOrder` | boolean | Maintain layer ordering |

### 5.2 Title Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide title |
| `text` | string | Title text |
| `fontSize` | number | Font size |
| `fontFamily` | string | Font family |
| `fontColor` | color object | Text color |
| `alignment` | string | "Left", "Center", "Right" |
| `titleWrap` | boolean | Enable wrapping |
| `bold` | boolean | Bold text |
| `italic` | boolean | Italic text |
| `underline` | boolean | Underlined text |

### 5.3 Background Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide background |
| `color` | color object | Background color |
| `transparency` | number (0-100) | Transparency % |

### 5.4 Border Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide border |
| `color` | color object | Border color |
| `radius` | number | Corner radius (px) |
| `width` | number | Border width (px) |

### 5.5 Shadow Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide shadow |
| `color` | color object | Shadow color |
| `position` | string | Shadow position |
| `preset` | string | Preset shadow style |

---

## 6. Chart-Specific Properties

### 6.1 Legend Properties

| Property | Type | Values/Description |
|----------|------|-------------------|
| `show` | boolean | Show/hide legend |
| `position` | string | Top, Bottom, Left, Right, TopCenter, BottomCenter, LeftCenter, RightCenter |
| `showTitle` | boolean | Show legend title |
| `titleText` | string | Legend title text |
| `labelColor` | color object | Label color |
| `legendColor` | color object | Alternative color property |
| `fontFamily` | string | Font family |
| `fontSize` | number | Font size |
| `bold` | boolean | Bold text |
| `italic` | boolean | Italic text |

### 6.2 Category Axis (X-Axis) Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide axis |
| `color` | color object | Axis line color |
| `labelColor` | color object | Label color |
| `fontSize` | number | Label font size |
| `fontFamily` | string | Label font family |
| `showAxisTitle` | boolean | Show title |
| `titleText` | string | Axis title |
| `titleColor` | color object | Title color |
| `titleFontSize` | number | Title font size |
| `titleFontFamily` | string | Title font family |
| `axisStyle` | string | showTitleOnly, showUnitOnly, showBoth |
| `preferredCategoryWidth` | number | Width per category |
| `maxMarginFactor` | number | Maximum margin |
| `innerPadding` | number | Inner padding |
| `concatenateLabels` | boolean | Concatenate multi-level |
| `labelDisplayUnits` | string | Auto, None, Thousands, Millions |

### 6.3 Value Axis (Y-Axis) Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show/hide axis |
| `axisScale` | string | Linear, Log |
| `start` | number | Axis start value |
| `end` | number | Axis end value |
| `labelColor` | color object | Label color |
| `fontSize` | number | Label font size |
| `fontFamily` | string | Font family |
| `labelDisplayUnits` | string | 0 (none), Thousands, Millions |
| `labelPrecision` | string/number | Decimal precision or Auto |
| `showAxisTitle` | boolean | Show title |
| `titleText` | string | Axis title |
| `titleColor` | color object | Title color |
| `titleFontSize` | number | Title font size |
| `titleFontFamily` | string | Title font family |
| `gridlineShow` | boolean | Show gridlines |
| `gridlineColor` | color object | Gridline color |
| `gridlineThickness` | number | Gridline thickness |
| `gridlineStyle` | string | solid, dashed, dotted |

### 6.4 Data Labels Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show labels |
| `color` | color object | Label color |
| `fontSize` | number | Font size |
| `fontFamily` | string | Font family |
| `labelDisplayUnits` | string | Display units |
| `labelPrecision` | number | Decimal places |
| `labelPosition` | string | Inside/Outside/Auto |
| `labelOrientation` | string | Horizontal/Vertical |
| `showBackground` | boolean | Show background |
| `backgroundColor` | color object | Background color |
| `backgroundTransparency` | number | Background transparency |

### 6.5 Data Point Properties

| Property | Type | Description |
|----------|------|-------------|
| `showAllDataPoints` | boolean | Show all points |
| `fill` | color object | Fill color |
| `defaultColor` | color object | Default color |

### 6.6 Zoom Slider Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show zoom slider |
| `showLabels` | boolean | Show labels |
| `showTooltip` | boolean | Show tooltip |

---

## 7. Table and Matrix Properties

### 7.1 Grid Properties

| Property | Type | Description |
|----------|------|-------------|
| `gridVertical` | boolean | Show vertical gridlines |
| `gridVerticalColor` | color object | Vertical gridline color |
| `gridVerticalWeight` | number | Vertical line weight |
| `gridHorizontal` | boolean | Show horizontal gridlines |
| `gridHorizontalColor` | color object | Horizontal line color |
| `gridHorizontalWeight` | number | Horizontal line weight |
| `rowPadding` | number | Row padding |
| `outlineColor` | color object | Outline color |
| `outlineWeight` | number | Outline weight |
| `textSize` | number | Text size |
| `imageHeight` | number | Image height in cells |

### 7.2 Total Properties

| Property | Type | Description |
|----------|------|-------------|
| `totals` | boolean | Show totals row |
| `fontColor` | color object | Total text color |
| `backColor` | color object | Total background |
| `outline` | string | Up, Down, Left, Right, None |
| `fontFamily` | string | Font family |
| `fontSize` | number | Font size |

### 7.3 Column Headers Properties

| Property | Type | Description |
|----------|------|-------------|
| `fontColor` | color object | Header text color |
| `backColor` | color object | Header background |
| `outline` | string | Header outline |
| `fontFamily` | string | Font family |
| `fontSize` | number | Font size |
| `wordWrap` | boolean | Enable word wrap |

### 7.4 Values/Cells Properties

| Property | Type | Description |
|----------|------|-------------|
| `fontColorPrimary` | color object | Primary text color |
| `backColorPrimary` | color object | Primary background |
| `fontColorSecondary` | color object | Alternate row text |
| `backColorSecondary` | color object | Alternate row background |
| `outline` | string | Cell outline |
| `urlIcon` | boolean | Show URL icons |
| `wordWrap` | boolean | Enable word wrap |

---

## 8. Slicer Properties

### 8.1 General Properties

| Property | Type | Description |
|----------|------|-------------|
| `outlineColor` | color object | Outline color |
| `outlineWeight` | number | Outline weight |
| `orientation` | string | horizontal, vertical |
| `responsive` | boolean | Responsive sizing |

### 8.2 Data Properties

| Property | Type | Description |
|----------|------|-------------|
| `mode` | string | Basic, Before, After, Between |
| `relativeRange` | string | Relative date range |
| `relativePeriod` | string | Relative period |

### 8.3 Selection Properties

| Property | Type | Description |
|----------|------|-------------|
| `selectAllCheckboxEnabled` | boolean | Show Select All |
| `singleSelect` | boolean | Single selection mode |

### 8.4 Header Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show header |
| `fontColor` | color object | Font color |
| `background` | color object | Background |
| `outline` | string | None, BottomOnly, etc. |
| `textSize` | number | Text size |
| `fontFamily` | string | Font family |

### 8.5 Items Properties

| Property | Type | Description |
|----------|------|-------------|
| `fontColor` | color object | Item font color |
| `background` | color object | Item background |
| `outline` | string | Item outline |
| `textSize` | number | Text size |
| `fontFamily` | string | Font family |

---

## 9. Card and KPI Properties

### 9.1 Card Callout Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show callout |
| `color` | color object | Callout color |
| `fontSize` | number | Font size (can exceed 60pt via theme) |
| `fontFamily` | string | Font family |
| `labelDisplayUnits` | string | Display units |
| `labelPrecision` | number | Decimal places |

### 9.2 Card Category Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show category label |
| `color` | color object | Category color |
| `fontSize` | number | Font size |
| `fontFamily` | string | Font family |

### 9.3 Gauge Properties

| Property | Type | Description |
|----------|------|-------------|
| `axis.show` | boolean | Show axis |
| `axis.min` | number | Minimum value |
| `axis.max` | number | Maximum value |
| `axis.target` | number | Target value |
| `dataPoint.fill` | color object | Fill color |
| `target.show` | boolean | Show target line |
| `target.color` | color object | Target color |
| `calloutValue.show` | boolean | Show callout |
| `calloutValue.color` | color object | Callout color |

---

## 10. Page and Shape Properties

### 10.1 Page Background Properties

| Property | Type | Description |
|----------|------|-------------|
| `color` | color object | Background color |
| `transparency` | number | Transparency (0-100) |
| `image.name` | string | Image name |
| `image.url` | string | Base64 encoded URL |
| `image.scaling` | string | Fit, Fill, Normal |

### 10.2 Shape Fill Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show fill |
| `fillColor` | color object | Fill color |
| `transparency` | number | Fill transparency |

### 10.3 Shape Line Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show line/border |
| `lineColor` | color object | Line color |
| `weight` | number | Line weight |
| `roundEdge` | number | Corner rounding |

---

## 11. Visual Header and Tooltip

### 11.1 Visual Header Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show header icons |
| `showVisualInformationButton` | boolean | Info button |
| `showVisualWarningButton` | boolean | Warning button |
| `showVisualErrorButton` | boolean | Error button |
| `showDrillRoleSelector` | boolean | Drill selector |
| `showDrillUpButton` | boolean | Drill up button |
| `showDrillToggleButton` | boolean | Drill toggle |
| `showDrillDownLevelButton` | boolean | Drill down button |
| `showDrillDownExpandButton` | boolean | Expand drill |
| `showPinButton` | boolean | Pin button |
| `showFocusModeButton` | boolean | Focus mode button |
| `showFilterRestatementButton` | boolean | Filter summary |
| `showSeeDataLayoutToggleButton` | boolean | Data toggle |
| `showOptionsMenu` | boolean | Options menu |
| `showTooltipButton` | boolean | Tooltip button |
| `foreground` | color object | Icon color |
| `background` | color object | Header background |
| `transparency` | number | Background transparency |

### 11.2 Tooltip Properties

| Property | Type | Description |
|----------|------|-------------|
| `show` | boolean | Show tooltips |
| `type` | string | Default, ReportPage |
| `titleFontColor` | color object | Title color |
| `valueFontColor` | color object | Value color |
| `backgroundColor` | color object | Background color |
| `fontSize` | number | Font size |
| `fontFamily` | string | Font family |

---

## 12. Filter Pane Properties

### 12.1 Filter Card Properties

| Property | Type | Description |
|----------|------|-------------|
| `$id (Available)` | object | Available filter styling |
| `$id (Applied)` | object | Applied filter styling |
| `backgroundColor` | color object | Card background |
| `foregroundColor` | color object | Text color |
| `borderColor` | color object | Border color |
| `inputBoxColor` | color object | Input field color |
| `transparency` | number | Background transparency |

---

## 13. Style Presets

Style presets allow named formatting variations. Available in Power BI Desktop March 2025+.

```json
"visualStyles": {
  "columnChart": {
    "*": {
      "stylePreset": [{ "name": "Default Preset" }]
    },
    "Custom Preset Name": {
      "legend": [{ "position": "Top" }],
      "valueAxis": [{ "gridlineColor": {"solid": {"color": "#FF0000"}} }]
    }
  }
}
```

---

## 14. Color Format Reference

### 14.1 Simple Hex Color
```json
"background": "#FFFFFF"
"dataColors": ["#118DFF", "#12239E"]
```

### 14.2 Solid Color Object
```json
"color": {
  "solid": {
    "color": "#118DFF"
  }
}
```

### 14.3 Theme Data Color Reference
```json
"color": {
  "solid": {
    "color": {
      "expr": {
        "ThemeDataColor": {
          "ColorId": 0,
          "Percent": 0
        }
      }
    }
  }
}
```

---

## 15. Complete Example Theme

```json
{
  "name": "Corporate Theme",
  "dataColors": [
    "#118DFF", "#12239E", "#E66C37", "#6B007B",
    "#E044A7", "#744EC2", "#D9B300", "#D64550"
  ],
  "background": "#FFFFFF",
  "foreground": "#252423",
  "tableAccent": "#118DFF",
  "firstLevelElements": "#252423",
  "secondLevelElements": "#605E5C",
  "thirdLevelElements": "#C8C6C4",
  "fourthLevelElements": "#EDEBE9",
  "secondaryBackground": "#F3F2F1",
  "backgroundLight": "#FAFAFA",
  "backgroundNeutral": "#E1DFDD",
  "foregroundNeutralSecondary": "#605E5C",
  "foregroundNeutralTertiary": "#A19F9D",
  "good": "#107C10",
  "neutral": "#797775",
  "bad": "#D83B01",
  "maximum": "#118DFF",
  "center": "#D9B300",
  "minimum": "#DEECF9",
  "null": "#FFFFFF",
  
  "textClasses": {
    "callout": {
      "fontSize": 45,
      "fontFace": "Segoe UI Light",
      "color": "#252423"
    },
    "title": {
      "fontSize": 12,
      "fontFace": "Segoe UI Semibold",
      "color": "#252423"
    },
    "header": {
      "fontSize": 12,
      "fontFace": "Segoe UI Semibold",
      "color": "#252423"
    },
    "label": {
      "fontSize": 10,
      "fontFace": "Segoe UI",
      "color": "#252423"
    }
  },
  
  "visualStyles": {
    "*": {
      "*": {
        "general": [{
          "responsive": true,
          "keepLayerOrder": true
        }],
        "title": [{
          "show": true,
          "fontColor": {"solid": {"color": "#252423"}},
          "fontSize": 12,
          "fontFamily": "Segoe UI Semibold"
        }],
        "background": [{
          "show": true,
          "color": {"solid": {"color": "#FFFFFF"}},
          "transparency": 0
        }],
        "border": [{
          "show": false,
          "color": {"solid": {"color": "#CCCCCC"}},
          "radius": 4
        }],
        "visualHeader": [{
          "show": true
        }]
      }
    },
    
    "barChart": {
      "*": {
        "legend": [{
          "show": true,
          "position": "Top",
          "showTitle": false,
          "fontFamily": "Segoe UI",
          "fontSize": 9
        }],
        "categoryAxis": [{
          "show": true,
          "fontSize": 9,
          "fontFamily": "Segoe UI",
          "showAxisTitle": false
        }],
        "valueAxis": [{
          "show": true,
          "fontSize": 9,
          "fontFamily": "Segoe UI",
          "showAxisTitle": false,
          "gridlineShow": true,
          "gridlineColor": {"solid": {"color": "#EDEBE9"}},
          "gridlineStyle": "solid"
        }],
        "labels": [{
          "show": false,
          "fontSize": 9,
          "fontFamily": "Segoe UI"
        }]
      }
    },
    
    "tableEx": {
      "*": {
        "grid": [{
          "gridVertical": true,
          "gridVerticalColor": {"solid": {"color": "#FFFFFF"}},
          "gridVerticalWeight": 1,
          "gridHorizontal": true,
          "gridHorizontalColor": {"solid": {"color": "#FFFFFF"}},
          "gridHorizontalWeight": 1,
          "rowPadding": 4,
          "outlineColor": {"solid": {"color": "#CCCCCC"}},
          "outlineWeight": 1,
          "textSize": 9
        }],
        "columnHeaders": [{
          "fontColor": {"solid": {"color": "#FFFFFF"}},
          "backColor": {"solid": {"color": "#118DFF"}},
          "fontSize": 10,
          "fontFamily": "Segoe UI Semibold"
        }],
        "values": [{
          "fontColorPrimary": {"solid": {"color": "#252423"}},
          "backColorPrimary": {"solid": {"color": "#FFFFFF"}},
          "fontColorSecondary": {"solid": {"color": "#252423"}},
          "backColorSecondary": {"solid": {"color": "#F3F2F1"}}
        }],
        "total": [{
          "totals": true,
          "fontColor": {"solid": {"color": "#252423"}},
          "backColor": {"solid": {"color": "#EDEBE9"}},
          "fontSize": 10,
          "fontFamily": "Segoe UI Semibold"
        }]
      }
    },
    
    "slicer": {
      "*": {
        "general": [{
          "responsive": true
        }],
        "header": [{
          "show": true,
          "fontColor": {"solid": {"color": "#252423"}},
          "textSize": 10,
          "fontFamily": "Segoe UI Semibold",
          "outline": "None"
        }],
        "items": [{
          "fontColor": {"solid": {"color": "#252423"}},
          "textSize": 10,
          "fontFamily": "Segoe UI",
          "outline": "None"
        }]
      }
    },
    
    "card": {
      "*": {
        "labels": [{
          "show": true,
          "color": {"solid": {"color": "#252423"}},
          "fontSize": 12,
          "fontFamily": "Segoe UI"
        }],
        "categoryLabels": [{
          "show": true,
          "color": {"solid": {"color": "#605E5C"}},
          "fontSize": 10,
          "fontFamily": "Segoe UI"
        }]
      }
    },
    
    "page": {
      "*": {
        "background": [{
          "color": {"solid": {"color": "#F3F2F1"}},
          "transparency": 0
        }]
      }
    }
  }
}
```

---

## 16. Resources

### Official Resources
- **Microsoft Docs:** https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-report-themes
- **Official JSON Schema:** https://github.com/microsoft/powerbi-desktop-samples/tree/main/Report%20Theme%20JSON%20Schema

### Community Resources
- **Theme Templates:** https://github.com/MattRudy/PowerBI-ThemeTemplates
- **PowerBI.Tips Generator:** https://themes.powerbi.tips/properties
- **BIBB Generator:** https://bibb.pro
- **Power UI Studio:** https://www.powerui.com
- **Curbal Theme Guide:** https://curbal.com

### Discovering Undocumented Properties
1. Rename PBIX to ZIP
2. Extract and examine `Report/Layout` JSON
3. Use VS Code with official schema for autocomplete

---

*Generated: January 2026*  
*Note: Power BI themes are continuously updated. Always check Microsoft documentation for latest properties.*
