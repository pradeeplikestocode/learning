# HTML & CSS – Cheat Code for Interviews

## ✅ HTML Essentials

### Basic Tags

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page Title</title>
  </head>
  <body>
    <h1>Heading</h1>
    <p>Paragraph</p>
    <a href="#">Link</a>
    <img src="image.jpg" alt="desc">
    <ul><li>Item</li></ul>
    <div>Container</div>
  </body>
</html>
```

### Semantic Tags

```html
<header>, <main>, <footer>, <article>, <section>, <nav>, <aside>
```

### Forms

```html
<form>
  <input type="text">
  <input type="email">
  <input type="submit">
</form>
```

---

## ✅ CSS Essentials

### Selectors

```css
*       /* all elements */
h1      /* by tag */
#id     /* by id */
.class  /* by class */
div > p /* child selector */
```

### Box Model

```css
box-sizing: border-box;
margin, border, padding, content
```

### Positioning

```css
position: static | relative | absolute | fixed | sticky;
top, bottom, left, right
```

### Flexbox

```css
display: flex;
justify-content: center | space-between | space-around;
align-items: center | flex-start | flex-end;
flex-direction: row | column;
```

### Grid

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
```

### Media Queries

```css
@media (max-width: 600px) {
  body { font-size: 14px; }
}
```

---

## ✅ CSS Hierarchy & Specificity

### Specificity Order

| Selector Type      | Specificity Score |
| ------------------ | ----------------- |
| Inline styles      | 1000              |
| IDs                | 100               |
| Classes/Attributes | 10                |
| Elements/Tags      | 1                 |

### Example

```css
h1 { color: red; }          /* Score: 1 */
.title { color: blue; }     /* Score: 10 */
#main { color: green; }     /* Score: 100 */
style="color: purple;"      /* Score: 1000 */
```

* The rule with the highest specificity wins.
* If specificity is the same, the last declared rule wins.

### 💡 Tips

* Avoid using inline styles; they have the highest specificity.
* Prefer class selectors for modular CSS.
* Use `!important` only when necessary – it overrides all.

---

## 💡 Pro Tips for Interviews

* Use semantic tags for accessibility and SEO.
* Understand CSS specificity: inline > id > class > tag.
* Prefer `rem`/`em` over `px` for responsive design.
* Flexbox for layout, Grid for structured components.
* Always use `box-sizing: border-box;` to avoid layout issues.
