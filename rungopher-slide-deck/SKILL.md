---
name: rungopher-slide-deck
description: "Create RunGopher branded slide decks from data or text. Use when the user wants to create presentations, slides, pitch decks, or convert content into a branded slide deck. Keywords: slide deck, presentation, slides, PowerPoint, PPTX, RunGopher branded, pitch deck, branded slides."
---

# RunGopher Slide Deck Creator

Create professional, on-brand slide decks that convert from HTML to PowerPoint PPTX format using RunGopher's brand guidelines.

## Overview

This skill generates HTML slides that follow RunGopher's brand identity and convert properly to PowerPoint format. It combines brand guidelines (colors, typography, tone) with technical requirements for HTML-to-PPTX conversion.

## Brand Identity

### Brand Purpose
RunGopher enables meaningful connections between organizations and their customers through automated, AI-powered two-way communication journeys.

### Brand Personality
- **Industry leaders**: Authority, maturity, and wisdom
- **Forerunners in technology**: Trusted system with security and performance
- **Exciting opportunities**: Transform marketing and customer engagement
- **Meaningful connections**: Genuine, personal, never spammy or cheesy

### Tone of Voice
- **Vibrant & Progressive**: Energy and optimism
- **Confident & Intelligent**: Professional, authoritative, knowledgeable

## Brand Colors

### Color Palette

| Color | Hex Code | RGB | Usage |
|-------|----------|-----|-------|
| Primary White | `#ffffff` | R:255 G:255 B:255 | Background, space |
| Secondary Sand | `#f1e8d6` | R:241 G:232 B:214 | Subtle backgrounds |
| Accent Coral | `#ff1c4d` | R:255 G:28 B:77 | Primary accent, CTAs |
| Accent Cobalt | `#3259fe` | R:50 G:89 B:254 | Secondary accent |
| Accent Black | `#000000` | R:0 G:0 B:0 | Body text |

### Color Usage Guidelines
- Use white space generously (50% white space recommended)
- Apply accent colors in small quantities to preserve visual weight
- 50% tints of Accent Coral and Accent Cobalt can offset vibrancy
- Body text should always be Accent Black (#000000)
- Stick roughly to the color proportions: primarily white with selective accent use

### CSS Variable Override
```css
:root {
  --color-primary: #ff1c4d;          /* Accent Coral */
  --color-secondary: #3259fe;        /* Accent Cobalt */
  --color-muted: #f1e8d6;            /* Secondary Sand */
  --color-surface: #ffffff;          /* Primary White */
  --color-surface-foreground: #000000; /* Accent Black */
}
```

## Typography

### Primary Typeface: Poppins Medium
- **Usage**: Headings, titles, display text
- **Weight**: Medium (600)
- **Fallback**: Arial, Helvetica, sans-serif (web-safe)

### Secondary Typeface: Recursive Sans Linear
- **Usage**: Body text, secondary content
- **Weight**: Light (300) and Medium Italic (500 italic)
- **Fallback**: Arial, Helvetica, sans-serif (web-safe)

**Note**: For HTML-to-PPTX conversion, use web-safe fonts. Poppins and Recursive Sans Linear should be referenced in brand guidelines, but use Arial/Helvetica in actual HTML code.

### Typography CSS Variables
```css
:root {
  --font-family-display: Arial, Helvetica, sans-serif;  /* Poppins Medium substitute */
  --font-weight-display: 600;
  --font-family-content: Arial, Helvetica, sans-serif;   /* Recursive Sans Linear substitute */
  --font-weight-content: 400;
}
```

## Critical HTML-to-PPTX Rules

### 1. Text Must Be in Proper HTML Tags
**CRITICAL**: All text MUST be inside `<p>`, `<h1>`-`<h6>`, `<ul>`, or `<ol>` tags.

✅ **CORRECT:**
```html
<div><p>Text here</p></div>
<div><h1>Title</h1></div>
<div><ul><li>Item</li></ul></div>
```

❌ **WRONG:**
```html
<div>Text here</div>
<!-- Text will NOT appear in PowerPoint! -->
```

### 2. Use `<ul>` or `<ol>` for Lists
Never use manual bullet symbols (•, -, *).

✅ **CORRECT:**
```html
<ul>
  <li>First item</li>
  <li>Second item</li>
</ul>
```

❌ **WRONG:**
```html
<p>• First item</p>
<p>- Second item</p>
```

### 3. Use Row/Col Classes (Not Flexbox)
Use `.row` and `.col` utility classes instead of `display: flex`.

✅ **CORRECT:**
```html
<div class="row">
  <p>Text here</p>
</div>
```

❌ **WRONG:**
```html
<div style="display: flex;">
  <p>Text here</p>
</div>
```

### 4. Web-Safe Fonts Only
Only use these fonts in HTML:
- Arial
- Helvetica
- Times New Roman
- Georgia
- Courier New
- Verdana
- Tahoma
- Trebuchet MS

### 5. Never Use `white-space: nowrap`
PowerPoint does NOT respect this CSS property. Use full-width text boxes for titles instead.

### 6. Slide Dimensions
All slides must be **960×540px** (16:9 aspect ratio):

```html
<body style="width: 960px; height: 540px;">
```

### 7. Slide Layout Zones

**Title Zone** (top 100px, y=0 to y=100):
- Reserved for slide title (`<h1>`)
- Title MUST span full width with 20px padding
- Wrap h1 in div with explicit width: 920px

```html
<div style="width: 920px; margin: 0 20px;">
  <h1>Title Text</h1>
</div>
```

**Content Zone** (y=110 to y=490):
- Main content area (380px height)
- Use 20-40px left/right margins
- Cards and boxes must be horizontally aligned

**Footnote Zone** (bottom 40px, y=500 to y=540):
- Reserved ONLY for footnotes, sources, disclaimers
- Must use **10pt font size**
- Keep brief

## Slide Template Structure

### Standard Content Slide
```html
<body class="col" style="width: 960px; height: 540px;">
  <!-- Title zone -->
  <div style="width: 920px; margin: 0 20px; padding-top: 20px;" class="fit">
    <h1 style="margin: 0;">Slide Title</h1>
  </div>

  <!-- Buffer (10px) -->
  
  <!-- Content zone -->
  <div class="fill-height row gap-lg" style="padding: 10px 40px 40px 40px;">
    <div class="col fill-width">
      <p>Main content goes here...</p>
      <ul>
        <li>First point</li>
        <li>Second point</li>
      </ul>
    </div>
  </div>

  <!-- Footnote zone (optional) -->
  <p style="position: absolute; bottom: 8px; left: 20px; font-size: 10pt; color: #666; margin: 0;">
    Source: Data from Q4 2024
  </p>
</body>
```

### Title Slide
```html
<body class="col center" style="width: 960px; height: 540px;">
  <h1 class="text-6xl" style="color: #ff1c4d;">RunGopher</h1>
  <h2 class="text-2xl" style="opacity: 0.7; margin-top: 20px;">Presentation Title</h2>
  <p class="text-lg" style="opacity: 0.5; margin-top: 40px;">Subtitle or Author Name</p>
</body>
```

### Two-Column Layout
```html
<body class="col" style="width: 960px; height: 540px;">
  <div style="width: 920px; margin: 0 20px; padding-top: 20px;" class="fit">
    <h1>Comparison</h1>
  </div>
  
  <div class="fill-height row gap-lg items-fill-width" style="padding: 10px 40px 40px 40px;">
    <div class="col">
      <h2>Left Column</h2>
      <p>Content for left side...</p>
    </div>
    <div class="col">
      <h2>Right Column</h2>
      <p>Content for right side...</p>
    </div>
  </div>
</body>
```

### Highlighted Content Card
```html
<div class="bg-primary p-6 rounded" style="margin: 20px 0;">
  <h2 class="text-primary-foreground">Key Message</h2>
  <p class="text-primary-foreground">Important content that stands out</p>
</div>
```

## Content Guidelines

### Writing Style
- **Vibrant & Progressive**: Use active voice, energetic language
- **Confident & Intelligent**: Be authoritative but accessible
- **Avoid**: Spammy language, cheesy marketing speak, jargon overload
- **Focus**: Meaningful connections, transformation, opportunities

### Visual Hierarchy
- Use generous white space (50% white space target)
- Apply accent colors (Coral/Cobalt) sparingly
- Use Sand (#f1e8d6) for subtle backgrounds
- Keep body text in Accent Black for readability

### Content Structure
- Start with clear value propositions
- Use bullet points for key benefits
- Include real examples and use cases
- End with clear next steps or calls to action

## Common Layout Patterns

### Stats/Metrics Slide
```html
<div class="fill-height" style="padding: 10px 40px 40px 40px;">
  <div class="row gap-lg" style="margin-bottom: 20px;">
    <div class="fill-width bg-muted p-6 rounded text-center">
      <p class="text-4xl text-primary">42%</p>
      <p class="text-lg">Growth Rate</p>
    </div>
    <div class="fill-width bg-muted p-6 rounded text-center">
      <p class="text-4xl text-primary">1,234</p>
      <p class="text-lg">Active Users</p>
    </div>
  </div>
</div>
```

### Feature List
```html
<div class="col gap-lg" style="padding: 20px 40px;">
  <div class="row gap-md items-center">
    <div class="bg-primary rounded" style="width: 40px; height: 40px; flex-shrink: 0;"></div>
    <div class="fill-width">
      <h3>Feature Name</h3>
      <p>Feature description goes here</p>
    </div>
  </div>
  <!-- Repeat for more features -->
</div>
```

## Best Practices

### Before Creating Slides
1. **Understand the audience**: Who are you presenting to?
2. **Define key messages**: What are the 3-5 main points?
3. **Gather data/content**: Have all information ready
4. **Plan flow**: Logical progression of ideas

### During Slide Creation
1. **One idea per slide**: Keep slides focused
2. **Use visual hierarchy**: Headings, body, accents
3. **Maintain brand consistency**: Colors, fonts, tone
4. **Test readability**: Ensure text is legible at presentation size
5. **Follow layout zones**: Respect title, content, footnote areas

### Technical Checklist
- [ ] All text is in `<p>`, `<h1>`-`<h6>`, `<ul>`, or `<ol>` tags
- [ ] Using `.row` and `.col` classes (not flexbox)
- [ ] No manual bullet symbols
- [ ] Only web-safe fonts (Arial, Helvetica)
- [ ] No `white-space: nowrap`
- [ ] Slide dimensions: 960×540px
- [ ] Title uses full-width wrapper (920px)
- [ ] Content fits within content zone (y=110 to y=490)
- [ ] Brand colors applied correctly
- [ ] Generous white space maintained

## Example Use Cases

### Converting Text to Slides
**Input**: "RunGopher helps companies connect with customers through AI-powered messaging. Key features: Automated journeys, Two-way communication, Personalization."

**Output**: Create a title slide and feature slide with proper HTML structure, brand colors, and layout.

### Creating a Pitch Deck
**Input**: Company overview, problem statement, solution, features, market opportunity

**Output**: Multi-slide presentation with:
- Title slide
- Problem statement slide
- Solution overview
- Feature highlights
- Market opportunity
- Call to action

### Data Visualization
**Input**: Statistics, metrics, or data points

**Output**: Slide with branded stat cards, proper spacing, and visual hierarchy.

## Troubleshooting

### Text Not Appearing in PowerPoint
- **Cause**: Text not wrapped in proper HTML tags
- **Solution**: Ensure all text is in `<p>`, `<h1>`-`<h6>`, `<ul>`, or `<ol>` tags

### Layout Breaking
- **Cause**: Using flexbox directly instead of utility classes
- **Solution**: Use `.row` and `.col` classes instead of `display: flex`

### Font Issues
- **Cause**: Non-web-safe fonts
- **Solution**: Use Arial or Helvetica instead

### Title Overflowing
- **Cause**: Title too long or using `white-space: nowrap`
- **Solution**: Ensure title is wrapped in 920px container, keep titles concise

### Color Not Rendering
- **Cause**: Background applied to text elements
- **Solution**: Apply backgrounds to block elements (`<div>`, not `<p>` or `<h1>`)

## Quick Reference

### Brand Colors (Hex Codes)
- Coral: `#ff1c4d`
- Cobalt: `#3259fe`
- Sand: `#f1e8d6`
- White: `#ffffff`
- Black: `#000000`

### Typography
- Headings: Arial/Helvetica, 600 weight (simulating Poppins Medium)
- Body: Arial/Helvetica, 400 weight (simulating Recursive Sans Linear)

### Slide Dimensions
- Width: 960px
- Height: 540px
- Aspect Ratio: 16:9

### Layout Zones
- Title: y=0 to y=100 (100px)
- Buffer: y=100 to y=110 (10px)
- Content: y=110 to y=490 (380px)
- Buffer: y=490 to y=500 (10px)
- Footnote: y=500 to y=540 (40px)
