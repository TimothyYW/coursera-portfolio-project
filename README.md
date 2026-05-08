# Little Lemon Restaurant — Home Page

A static home page built for the **Meta Front-End Developer** Coursera course portfolio project.  
The client is **Little Lemon**, a fictional Mediterranean restaurant based in Chicago.

---

## Live Preview

Open `index.html` directly in your browser, or enable GitHub Pages under  
**Settings → Pages → Branch: main → / (root)** to get a public URL.

---

## What I Built

| Section | Description |
|---|---|
| Header | Sticky navigation bar with the Little Lemon logo and 4 nav links |
| Hero Banner | Full-width promotional section with headline, tagline, CTA button, and animated lemon graphic |
| Weekly Specials | Three-column card grid showcasing menu items with images, prices, and order links |
| Footer | Two-column layout — brand logo on the left, contact and copyright info on the right |

---

## Concepts Learned

### HTML — Semantic Structure

Semantic tags give meaning to content beyond just visual appearance. Screen readers and search engines rely on them.

```html
<header>   <!-- site identity and navigation -->
<nav>      <!-- navigation links -->
<main>     <!-- primary page content -->
<section>  <!-- a thematic grouping of content -->
<article>  <!-- self-contained piece of content (each menu card) -->
<footer>   <!-- site-wide closing info -->
```

### CSS Layout — Grid vs Flexbox

Both are used in this project for different purposes:

**CSS Grid** — best for two-dimensional layouts (rows AND columns)
```css
/* Page skeleton */
body {
  display: grid;
  grid-template-rows: auto 1fr auto; /* header | main | footer */
}

/* Three-column specials section */
.specials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}
```

**Flexbox** — best for one-dimensional layouts (a single row OR column)
```css
/* Header: logo left, nav right */
.header-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Footer: two columns side by side */
.footer-inner {
  display: flex;
  gap: 52px;
}
```

**Rule of thumb:**
- Use **Grid** when you control both rows and columns.
- Use **Flexbox** when you control a single axis (a row of buttons, a column of items).

---

### CSS Custom Properties (Variables)

Variables let you define values once and reuse them everywhere. Changing a brand colour only requires one edit.

```css
:root {
  --color-green:  #495E57;
  --color-yellow: #F4CE14;
  --color-salmon: #EE9972;
}

/* Usage */
.hero {
  background-color: var(--color-green);
}
```

---

### Pseudo-classes — Interactivity Without JavaScript

Pseudo-classes apply styles when an element is in a certain state.

```css
/* Highlight nav link on hover */
.nav-links a:hover {
  color: var(--color-green);
  border-bottom-color: var(--color-yellow);
}

/* Lift card on hover */
.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.14);
}
```

Common pseudo-classes:

| Pseudo-class | Triggers when… |
|---|---|
| `:hover` | Mouse moves over the element |
| `:focus` | Element receives keyboard/click focus |
| `:active` | Element is being clicked |
| `:visited` | A link has been visited |
| `:first-child` | Element is the first child of its parent |

---

### CSS Transitions

Transitions animate a property change smoothly instead of jumping instantly.

```css
.card {
  transition: transform 0.25s, box-shadow 0.25s;
}
/* When .card:hover changes transform/box-shadow, it animates over 0.25 seconds */
```

Syntax: `transition: <property> <duration> <timing-function>;`

---

### CSS Keyframe Animations

Keyframes define a sequence of states an element moves through over time.

```css
@keyframes float {
  0%,  100% { transform: translateY(0);     }
  50%        { transform: translateY(-12px); }
}

.hero-image img {
  animation: float 3s ease-in-out infinite;
  will-change: transform; /* tells the browser to prepare a GPU layer */
}
```

**`will-change: transform`** — a performance hint that moves the element onto its own compositor layer so the animation runs on the GPU instead of repainting the whole page.

---

### `object-fit` for Images

Controls how an `<img>` fills its container without distortion.

```css
.card-img {
  height: 160px;
  width: auto;
  object-fit: contain; /* scales image to fit, preserving aspect ratio */
}
```

| Value | Behaviour |
|---|---|
| `contain` | Scales to fit inside the box — no cropping |
| `cover` | Scales to fill the box — may crop edges |
| `fill` | Stretches to fill — distorts if aspect ratio differs |

---

## File Structure

```
coursera-portfolio-project/
├── index.html      # Page structure and content
├── styles.css      # All styling, layout, and animations
└── imagies/        # Brand assets (logos and lemon illustrations)
    ├── Asset 7@4x.png    dark green lemon illustration
    ├── Asset 9@4x.png    yellow lemon illustration
    ├── Asset 14@4x.png   horizontal logo (dark)
    ├── Asset 16@4x.png   horizontal logo (colour) — used in header
    ├── Asset 18@4x.png   square logo (dark)
    └── Asset 20@4x.png   square logo (colour) — used in footer
```

---

## Colour Palette

| Name | Hex | Used for |
|---|---|---|
| Green | `#495E57` | Hero background, hover accents |
| Yellow | `#F4CE14` | Buttons, h1, dessert card |
| Salmon | `#EE9972` | Price text, bruschetta card |
| Section BG | `#EDEFEE` | Specials section background |
| Carbon | `#333333` | Body text |

---

## Course

**Meta Front-End Developer Professional Certificate**  
[Introduction to Front-End Development](https://www.coursera.org/learn/introduction-to-front-end-development) — Coursera
