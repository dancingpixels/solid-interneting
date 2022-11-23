# Floats

- Block elements always appear vertically one after another, effectively limiting us to a single-column layout.
- `Floats` let you put block-level elements side-by-side instead of on top of each other.
- It lets us build all sorts of layouts, including sidebars, multi-column pages, grids, and magazine-style articles with text flowing around an image.
- Float-based layouts have mostly been replaced with Flexbox in modern websites.
- Floats alter the default layout of a page.

- Each block-level element fills 100% of its parent elements' width, and they appear vertically one after another, essentially limiting us to a single-column layout.

# Floating and Element

- The CSS `float` property gives us control over the *horizontal* position of an element. 
- We are telling the browser to align it to the left side or right side of the page. 

```css
.sidebar {
  float: left;                
  width: 200px;
  height: 300px;
}
```

- it also tells surrounding elements that they can flow *around* the element instead of beginning underneath it. 
- if you're overriding a float declaration, you can cancel it with the `none` value. 

```css
float: right;  /* Right-aligned */
float: none;   /* Revert to default flow */
```

# Clearing floats

- “Clearing" a float is when we tell a block to ignore any floats that appear before it.
-  Instead of flowing around the floated box, a cleared element always appears after any floats.
-  It's like forcing a box back into the default vertical flow of the page.

```css
.footer {
  clear: both;            
}
```

# Floats for content

