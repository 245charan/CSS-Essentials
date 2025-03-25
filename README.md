# CSS Essentials

Flex-to-Grid correlation cheat sheet:

### 1. Parent Container Equivalents
| Flex Layout           | Grid Equivalent                | Notes |
|-----------------------|---------------------------------|-------|
| `display: flex`       | `display: grid`                | Start here |
| `flex-direction`      | `grid-auto-flow` + `grid-template` | Use `grid-template-columns/rows` for explicit control |
| `justify-content`     | `justify-content`              | Same property name! |
| `align-items`         | `align-items`                  | Same property name! |
| `gap: 20px`           | `gap: 20px`                    | Same syntax! |
| `flex-wrap: wrap`     | `grid-template-columns: repeat(auto-fit, minmax())` | More powerful alternative |

### 2. Child Items Equivalents
| Flex Item            | Grid Item                | Notes |
|----------------------|--------------------------|-------|
| `flex: 1`           | `grid-column: span X` + fr units | Use fractional units (`1fr`) |
| `order: 2`          | `order: 2`               | Same property! |
| `align-self`        | `align-self`             | Same property! |
| `margin: auto`      | `margin: auto`           | Same centering trick |

### 3. Common Patterns
**Flex: Equal width columns**
```css
.container {
  display: flex;
  gap: 20px;
}
.item { flex: 1 }
```

**Grid Equivalent:**
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(0, 1fr));
  gap: 20px;
}
```

**Flex: Holy Grail Layout**
```css
.container {
  display: flex;
  flex-direction: column;
}
.main-content { flex: 1 }
```

**Grid Equivalent:**
```css
.container {
  display: grid;
  grid-template-rows: auto 1fr auto;
  min-height: 100vh;
}
```

### 4. Pro Tips
1. **Fractional Units** are your new best friend (`1fr = flex-grow: 1`)
2. **Grid Areas** beat nested flex containers:
```css
.container {
  grid-template-areas: "header header"
                       "sidebar main";
}
```
3. **Responsive Magic**:
```css
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
```

### 5. When to Use Which
- **Flexbox**: Single-axis layouts (navigation bars, simple lists)
- **Grid**: Complex 2D layouts (entire pages, card grids, overlapping elements)

You can mix both! Grid for overall layout, Flexbox for internal components.
