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

## Brand Logo

### Logo Usage Guidelines

**CRITICAL**: The RunGopher logo MUST be included on EVERY slide for brand consistency. This is mandatory, not optional.

**Logo Requirements:**
- **MUST appear on every slide** in the presentation
- **Standard placement**: Top-right corner (20px from top, 20px from right)
- **Alternative placement**: Bottom-right corner (if top-right conflicts with content)
- **Size**: Approximately 20-24px font size for text-based logo

**Logo Variations:**
- **Inline logo** (primary): Use for header/footer areas
- **Stacked logo**: Use when vertical space is limited
- **Wordmark**: Use when iconmark is too small
- **Iconmark**: Use only when "RunGopher" text appears nearby

**Logo Placement:**
- **Header**: Top-right corner (recommended for most slides)
- **Footer**: Bottom-right corner (alternative option)
- **Clear space**: Maintain clear space equal to the height of the "o" in RunGopher

**Logo on Backgrounds:**
- **White logo** on navy/dark backgrounds (Accent Cobalt or Navy)
- **Black logo** on light backgrounds (White or Sand)
- Ensure sufficient contrast for visibility

**Implementation:**
Since logo files need to be provided separately, use placeholder instructions or SVG/text-based logo representation in HTML. The logo should be positioned absolutely in the header/footer area.

### Logo HTML Template
```html
<!-- Logo in header (top-right) -->
<div style="position: absolute; top: 20px; right: 20px; width: 120px; height: auto;">
  <img src="rungopher-logo-white.svg" alt="RunGopher" style="width: 100%; height: auto;" />
</div>

<!-- Or text-based logo placeholder -->
<div style="position: absolute; top: 20px; right: 20px;">
  <h2 style="color: #ffffff; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 24px;">RunGopher</h2>
</div>
```

## Brand Colors

### Color Palette

| Color | Hex Code | RGB | Usage |
|-------|----------|-----|-------|
| Primary White | `#ffffff` | R:255 G:255 B:255 | Background, space |
| Secondary Sand | `#f1e8d6` | R:241 G:232 B:214 | Subtle backgrounds |
| Accent Coral | `#ff1c4d` | R:255 G:28 B:77 | Primary accent, CTAs |
| Accent Cobalt | `#3259fe` | R:50 G:89 B:254 | Secondary accent (bright blue) |
| Navy | `#1a3a8c` | R:26 G:58 B:140 | Dark navy for backgrounds with logo |
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
  --color-navy: #1a3a8c;            /* Navy for backgrounds */
}
```

### Navy Background Option

For slides with navy backgrounds (especially title slides or section dividers):
- Use Navy color (`#1a3a8c`) for full slide backgrounds
- Place white RunGopher logo in top-right corner
- Use white text for headings and content
- Maintain brand consistency while creating visual impact

## Typography

### Brand Typography Guidelines

**Primary Typeface: Poppins Medium**
- **Usage**: All headings (`<h1>`, `<h2>`, `<h3>`, etc.), titles, display text
- **Weight**: Medium (600)
- **Web-Safe Substitute**: Arial, Helvetica, sans-serif with font-weight: 600

**Secondary Typeface: Recursive Sans Linear**
- **Usage**: Body text (`<p>`), list items (`<li>`), secondary content
- **Weight**: Light (300) for regular text
- **Web-Safe Substitute**: Arial, Helvetica, sans-serif with font-weight: 400

### REQUIRED: Typography Implementation

**CRITICAL**: PowerPoint does NOT respect CSS variables. Every slide MUST use EXPLICIT font-family declarations. Use direct font-family styles, NOT CSS variables.

**PowerPoint Font Requirements:**
- **MUST use Arial** (not Calibri, not CSS variables)
- **Headings**: `font-family: Arial, sans-serif; font-weight: 600;`
- **Body text**: `font-family: Arial, sans-serif; font-weight: 400;`
- Apply font-family directly to elements via inline styles or direct CSS selectors

```html
<head>
  <style>
    /* RunGopher Typography - REQUIRED for all slides */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    /* Headings - Poppins Medium substitute (Arial, 600 weight) */
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    /* Body text - Recursive Sans Linear substitute (Arial, 400 weight) */
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    /* Override any default fonts */
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
```

**IMPORTANT**: Always add inline `style="font-family: Arial, sans-serif;"` to headings and paragraphs as a fallback, since PowerPoint may ignore CSS rules.

### Typography Application Rules

1. **ALWAYS include the style tag** in the `<head>` of every slide HTML with direct font-family declarations
2. **ALWAYS add inline styles** to headings: `<h1 style="font-family: Arial, sans-serif; font-weight: 600;">`
3. **ALWAYS add inline styles** to body text: `<p style="font-family: Arial, sans-serif; font-weight: 400;">`
4. **PowerPoint Compatibility**: 
   - PowerPoint does NOT support CSS variables (`var(--font-family)`)
   - PowerPoint defaults to Calibri if fonts aren't explicitly set
   - Use `!important` in CSS and inline styles as fallback
5. **Font weights**: 
   - Headings: 600 (bold/medium) - Arial
   - Body text: 400 (regular/normal) - Arial
6. **Never use**: Calibri, CSS variables, or font weights other than 400 (body) or 600 (headings) unless explicitly needed

## Critical HTML-to-PPTX Rules

### 0. Consistent Background Colors - MANDATORY
**CRITICAL**: ALL slides in a presentation MUST use the SAME background color throughout. Do NOT mix navy and white backgrounds.

**Background Color Rules:**
- **Choose ONE background color** for the entire presentation at the start
- **Apply it consistently** to every slide
- **Options**:
  - **White** (`background-color: #ffffff;`) - Recommended for most presentations
  - **Navy** (`background-color: #1a3a8c;`) - Use for full navy theme
  - **Sand** (`background-color: #f1e8d6;`) - Use for subtle theme
- **DO NOT** switch between colors mid-presentation
- **Exception**: Title slide can be navy while rest are white (or vice versa), but this must be consistent across all title slides vs content slides

**Implementation:**
- Set background on `<body>` tag: `<body style="background-color: #ffffff; ...">`
- Ensure logo color matches background (white logo on navy, black logo on white)

### 1. Logo MUST Be Included on Every Slide
**CRITICAL**: Every slide MUST include the RunGopher logo in the top-right corner. This is mandatory for brand consistency.

**Logo Template (copy to every slide):**
```html
<!-- RunGopher Logo - Top Right (REQUIRED on every slide) -->
<div style="position: absolute; top: 20px; right: 20px;">
  <h2 style="color: #000000; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
</div>
```

**Logo Color Rules:**
- **White backgrounds**: Use black logo (`color: #000000;`)
- **Navy backgrounds**: Use white logo (`color: #ffffff;`)
- **Sand backgrounds**: Use black logo (`color: #000000;`)

### 2. Typography MUST Be Included in Every Slide
**CRITICAL**: Every slide HTML MUST include a `<head>` section with `<style>` tag containing the RunGopher typography rules. Without this, typography will not be applied correctly.

See the "Typography" section above for the complete required `<head>` and `<style>` block that must be included in every slide.

### 3. Text Must Be in Proper HTML Tags
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

### 4. Use `<ul>` or `<ol>` for Lists
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

### 5. Use Row/Col Classes (Not Flexbox)
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

### 6. Web-Safe Fonts Only
Only use these fonts in HTML:
- Arial
- Helvetica
- Times New Roman
- Georgia
- Courier New
- Verdana
- Tahoma
- Trebuchet MS

### 7. Never Use `white-space: nowrap`
PowerPoint does NOT respect this CSS property. Use full-width text boxes for titles instead.

### 8. Slide Dimensions
All slides must be **960×540px** (16:9 aspect ratio):

```html
<body style="width: 960px; height: 540px;">
```

### 9. Slide Layout Zones

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

**IMPORTANT**: All slides MUST have:
1. Consistent background color (choose white OR navy for entire presentation)
2. RunGopher logo in top-right corner
3. Proper typography styles

### Standard Content Slide (White Background - Default)
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* RunGopher Typography - REQUIRED */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
<body class="col" style="width: 960px; height: 540px; background-color: #ffffff; position: relative;">
  <!-- RunGopher Logo - Top Right (REQUIRED on every slide) -->
  <div style="position: absolute; top: 20px; right: 20px;">
    <h2 style="color: #000000; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
  </div>
  
  <!-- Title zone -->
  <div style="width: 920px; margin: 0 20px; padding-top: 20px;" class="fit">
    <h1 style="margin: 0; font-family: Arial, sans-serif; font-weight: 600;">Slide Title</h1>
  </div>

  <!-- Buffer (10px) -->
  
  <!-- Content zone -->
  <div class="fill-height row gap-lg" style="padding: 10px 40px 40px 40px;">
    <div class="col fill-width">
      <p style="font-family: Arial, sans-serif; font-weight: 400;">Main content goes here...</p>
      <ul>
        <li style="font-family: Arial, sans-serif; font-weight: 400;">First point</li>
        <li style="font-family: Arial, sans-serif; font-weight: 400;">Second point</li>
      </ul>
    </div>
  </div>

  <!-- Footnote zone (optional) -->
  <p style="position: absolute; bottom: 8px; left: 20px; font-size: 10pt; color: #666; margin: 0;">
    Source: Data from Q4 2024
  </p>
</body>
</html>
```

### Title Slide (White Background - Default)
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* RunGopher Typography - REQUIRED */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
<body class="col center" style="width: 960px; height: 540px; background-color: #ffffff; position: relative;">
  <!-- RunGopher Logo - Top Right (REQUIRED on every slide) -->
  <div style="position: absolute; top: 20px; right: 20px;">
    <h2 style="color: #000000; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
  </div>
  
  <h1 class="text-6xl" style="color: #ff1c4d; font-family: Arial, sans-serif; font-weight: 600;">RunGopher</h1>
  <h2 class="text-2xl" style="opacity: 0.7; margin-top: 20px; font-family: Arial, sans-serif; font-weight: 600;">Presentation Title</h2>
  <p class="text-lg" style="opacity: 0.5; margin-top: 40px; font-family: Arial, sans-serif; font-weight: 400;">Subtitle or Author Name</p>
</body>
</html>
```

**NOTE**: If using navy backgrounds, change `background-color: #ffffff;` to `background-color: #1a3a8c;` and logo color to `#ffffff;` - but use the SAME background color for ALL slides in the presentation.

### Title Slide (Navy Background - Recommended)
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* RunGopher Typography - REQUIRED */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
<body class="col center" style="width: 960px; height: 540px; background-color: #1a3a8c; position: relative;">
  <!-- RunGopher Logo - Top Right (White) -->
  <div style="position: absolute; top: 20px; right: 20px;">
    <h2 style="color: #ffffff; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
  </div>
  
  <h1 class="text-6xl" style="color: #ffffff; margin-top: 80px; font-family: Arial, sans-serif; font-weight: 600;">RunGopher</h1>
  <h2 class="text-2xl" style="color: #ffffff; opacity: 0.9; margin-top: 20px; font-family: Arial, sans-serif; font-weight: 600;">Presentation Title</h2>
  <p class="text-lg" style="color: #ffffff; opacity: 0.7; margin-top: 40px; font-family: Arial, sans-serif; font-weight: 400;">Subtitle or Author Name</p>
</body>
</html>
```

### Two-Column Layout
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* RunGopher Typography - REQUIRED */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
<body class="col" style="width: 960px; height: 540px; background-color: #ffffff; position: relative;">
  <!-- RunGopher Logo - Top Right (REQUIRED on every slide) -->
  <div style="position: absolute; top: 20px; right: 20px;">
    <h2 style="color: #000000; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
  </div>
  
  <div style="width: 920px; margin: 0 20px; padding-top: 20px;" class="fit">
    <h1 style="font-family: Arial, sans-serif; font-weight: 600;">Comparison</h1>
  </div>
  
  <div class="fill-height row gap-lg items-fill-width" style="padding: 10px 40px 40px 40px;">
    <div class="col">
      <h2 style="font-family: Arial, sans-serif; font-weight: 600;">Left Column</h2>
      <p style="font-family: Arial, sans-serif; font-weight: 400;">Content for left side...</p>
    </div>
    <div class="col">
      <h2 style="font-family: Arial, sans-serif; font-weight: 600;">Right Column</h2>
      <p style="font-family: Arial, sans-serif; font-weight: 400;">Content for right side...</p>
    </div>
  </div>
</body>
</html>
```

### Section Divider Slide (Navy Background - Use Only If Entire Presentation Is Navy)
```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* RunGopher Typography - REQUIRED */
    /* CRITICAL: Use direct font-family, NOT CSS variables - PowerPoint doesn't support CSS variables */
    
    h1, h2, h3, h4, h5, h6 {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 600 !important;
    }
    
    p, li, span, div {
      font-family: Arial, Helvetica, sans-serif !important;
      font-weight: 400 !important;
    }
    
    body {
      font-family: Arial, Helvetica, sans-serif !important;
    }
  </style>
</head>
<body class="col center" style="width: 960px; height: 540px; background-color: #1a3a8c; position: relative;">
  <!-- RunGopher Logo - Top Right (White) -->
  <div style="position: absolute; top: 20px; right: 20px;">
    <h2 style="color: #ffffff; font-family: Arial, sans-serif; font-weight: 600; margin: 0; font-size: 20px;">RunGopher</h2>
  </div>
  
  <h1 class="text-5xl" style="color: #ffffff; margin-top: 150px; font-family: Arial, sans-serif; font-weight: 600;">Section Title</h1>
  <p class="text-xl" style="color: #ffffff; opacity: 0.8; margin-top: 30px; font-family: Arial, sans-serif; font-weight: 400;">Section subtitle or description</p>
</body>
</html>
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
