# Interneting is *not* hard 

## HTML Elements Types

There are 2 types of  major HTML elements:

1. `block-level` elements also know as `flow` elements.

   - `block level` elements are always drawn on a new line.

   ```html
   <p>, <h1>...</h1>, <ol>, <li>...</li>
   ```

2. `inline` elements known as `phrasing` elements.

   - `inline` elements can affect sections of text anywhere within a line.

   ```html
   <em>...</em> <!-- affects the span of a text inside a paragraph -->
   <strong>...</strong>
   ```

## Self Closing Elements

Some elements can be `empty` or `self-closing`. Line breaks and horizontal rules are the most common empty elements you’ll find.

```html
<br/> <!-- line break -->
<hr/> <!-- thematic break -->
<img/>
```

## Links

Absolute, relative, and root-relative links refer to the value of the `href` attribute. Absolute links

### Absolute Links

`Absolute` links are the most detailed way you can refer to a web resource. They start with the “scheme” (typically `http://` or `https://`), followed by the domain name of the website, then the path of the target web page.

```html
<a href='https://developer.mozilla.org/en-US/docs/HTML'>Mozilla Developer Network
</a>
```

They are best used for directing users to a new website.

### Relative Links

`Relative` links point to another file in your website from the vantage point of the file you’re editing. It’s implied that the scheme and domain name are the same as the current page, so the only thing you need to supply is the path.

```html
<li> Relative links like to our <a href='misc/extras.html'>Extras page.</a> 
</li>
```

### Root-Relative Links

`Root-relative` links are similar to `relative` links but instead of being relative to the current page, they’re relative to the “root” of the entire website. 

```html
<a href="/">Home page</a>
```

## Images

### Image Formats

There are 4 main image formats in use on the web.

- JPG Images - `jpg`images are great for photos and images with lots of gradients in them. 
- GIF Images - `GIF`s are the go-to option for simple animations, but the trade off is that they’re somewhat limited in terms of color palette—never use them for photos.
- GIF Images - `GIF`s are the go-to option for simple animations.
- PNG Images - `PNG`s are great for anything that’s not a photo or animated. For photos, a `PNG` file of the same quality (as perceived the human eye) would generally be bigger than an equivalent `JPG` file. They are excellent fit for icons, technical diagrams, logos, etc.
- SVG Images  - a vector-based graphics format, meaning it can scale up or down to *any* dimension without loss of quality. This property makes `SVG` images a wonderful tool for responsive design. 

### Image Dimensions

- By default, the `<img/>` element uses the inherit dimensions of its image file. 
- The `width` attribute sets an explicit dimension for the image.
- Setting both `width` and `height` attributes will cause the image to scale proportionally, while defining both will stretch the image. 
- Dimension values are specified in pixels, and you should never include a unit (e.g., `width='75px'` would be incorrect).

## Reserved Characters

The `<`, `>`, and `&` characters are called “reserved characters” because they aren’t allowed to be inserted into an HTML document without being encoded. This is because they mean something in the HTML syntax: `<` begins a new tag, `>` ends a tag, `&` sets off an HTML entity. 

```html
<!-- There are three reserved characters in HTML: -->
&lt; &gt; &amp; 
<!-- You should always use HTML entities for these three characters, -->
```

Entities always begin with an ampersand (`&`) and end with a semicolon (`;`). In between, you put a special code that your browser will interpret as a symbol. In this case, it interprets `lt`, `gt`, and `amp` as less-than, greater-than, and ampersand symbols, respectively.

## Hello CSS

### Units of Measurement

Many CSS properties require a unit of measurement. There are lots of unit measurement available, but the common are `px` pixel and `em` - pronounced like the letter _m_.

The `em` unit is very useful for defining sizes relative to some base font. it scales the measurement up or down to match the base font defined.



![em-units](images/em-units.png)

### Selecting multiple elements

We can select multiple HTML elements in the same CSS rule by separating them with commas. 

```css
h1, h2, h3, h4, h5, h6 {
  font-family: "Helvetica", "Arial", sans-serif;
}
```

### Defining Fonts

`font-family` is a CSS property that defines the typeface for whatever element you selected. It accepts multiple values because not all users will have the same fonts installed. 

```css
font-family: "Helvetica", "Arial", sans-serif;
```

### List Styles

The `list-style-type` property lets you alter the bullet icon used for `<li>` elements. You’ll typically want to define it on the parent `<ul>` or `<ol>` element:

```css
ul {
  list-style-type: circle;
}

ol {
  list-style-type: lower-roman;
}
```

### Underlines

The `text-decoration` property determines whether text is underlined or not. By setting it to `none`, we can remove the default underline from all of our links. 

```css
a {
  text-decoration: none;
}
```

### Font Weight and Styles

The `font-weight` property defines the “boldness” of the text in an element, and the `font-style` property indicates whether it’s italicized or not.

```css
h1, h2, h3, h4, h5, h6 {
  font-family: "Helvetica", "Arial", sans-serif;
  font-weight: normal;                              
}
```

### The Cascade

The `cascading` part of CSS is due to the fact that rules cascade down from multiple sources.

The CSS hierarchy for every web page is:

- The browser's default stylesheet

- User-defined stylesheets

- External stylesheets (that's us)

- Page-specific styles (that's also us)

- Inline styles (that could be us, but it never should be)

Styles defined in each subsequent step *override* previous ones.

An example of inline styling

```css
<a href='nowhere.html'
   style='color: #990000; text-decoration: line-through;'>obsolete link
</a>
```

> Inline styles should be avoided at all costs because they make it impossible to alter styles from an external stylesheet. 

## The Box Model

> A friendly introduction to padding, borders, and margins.

- The `CSS box model` is a set of rules that define how every web page on the Internet is rendered. 
- CSS treats each element in your HTML document as a “box” with a bunch of different properties that determine where it appears on the page. 

### Block Elements and Inline Elements

Each HTML element rendered on the screen is a box, and they come in two flavors: `block` boxes and `inline` boxes.

![Diagram: comparison of block boxes with inline boxes](images/inline-vs-block-boxes.png)

All the HTML elements have a default type of box:

- `<h1>` and `<p>` are block-level elements,
-  while `<em>` and `<strong>` are inline elements. 

### Block Elements

- **Block boxes** always appear **below** the previous block element. This is the “natural” or “static” flow of an HTML  document when it gets rendered by a web browser.
- The **width of block boxes** is set automatically based on the width of its parent container.
  - In this case, our blocks are always the width of the browser window.
- The default **height of block boxes** is based on the content it contains. 
  - When you narrow the browser window, the height of block elements adjusts accordingly.

### Inline Elements

- **Inline boxes** don't affect **vertical spacing**. 
  - They're not for determining layout—they're for styling stuff *inside* of a block.
- The **width of inline boxes** is based on the content it contains, not the width of the parent element.

### Changing Box behaviour

We can override the default box type of HTML elements with the CSS `display ` property. For example, if we wanted to make our `<em>` and `<strong>` elements blocks instead of inline elements.

```css
em, strong {
  display: block;
}
```

This comes in handing when you are trying to turn `<a>` elements into buttons or format `<img>` elements - both of which are inline by default. 

### Content, padding, border, and margin

The `CSS box model` is a set of rules that determine the dimensions of every element in a web page. It gives each box (both inline and block) four properties:

- **Content** – The text, image, or other media content in the element.
- **Padding** – The space between the box's content and its border.
- **Border** – The line between the box's padding and margin.
- **Margin** – The space between the box and surrounding boxes.

Together, this is everything a browser needs to render an element’s box. The `content` is the only property with semantic value - hence it's authored in HTML. The remaining properties are purely presentational, so they are defined by CSS.

<img src="images/css-box-model.png" style="zoom:50%;" />

### Padding

The `padding` property defines the padding for the selected element:

```css
h1 {
  padding: 50px;
}
```

This adds 50 pixels to *each side* of the `<h1>` heading. 

Sometimes you’ll only want to style one side of an element. For that, CSS provides the following properties:

```css
p {
  padding-top: 20px;
  padding-bottom: 20px;
  padding-left: 10px;
  padding-right: 10px;
}
```

You can use any unit for the padding of an element, not just pixels.

CSS provides an alternative “shorthand” form of the `padding` property that lets you set the top/bottom and left/right padding with only one line of CSS. 

- When you provide *two* values to the `padding` property, it's interpreted as the vertical and horizontal padding values, respectively.

- This means that our previous rule can be rewritten as:

  ```css
  p {
    padding: 20px 10px;  /* Vertical  Horizontal */
  }
  ```

- Alternatively, if you provide *four* values, you can set the padding for each side of an element individually. The values are interpreted clockwise, starting at the top

- ```css
  p {
    padding: 20px 0 20px 10px;  /* Top  Right  Bottom  Left */
  }
  ```

### Borders

- A line drawn around the content and padding of an element.
- We set borders by defining the:
  - size
  - style, 
  - color

```css
h1 {
    border: 1px solid #5D6063;
}
```

- Like `padding`, there are `-top`, `-bottom`, `-left`, and `-right` variants for the `border` property:

```css
border-bottom: 1px solid #5D6063;
```



> Borders are common design elements, but they're also invaluable for debugging. When you're not sure how a box is being rendered, add a `border: 1px solid red;` declaration to it. This will clearly show the box's padding, margin, and overall dimensions with just a single line of CSS. After you figured out why your stuff is broken, simply delete the rule.

### Margins

- Margins define the he space between a box and its surrounding boxes.
- it also accepts the same shorthand formats as `padding`.

```css
p {
  margin-bottom: 50px;         
}
```

### Margins on Inline Elements

One of the starkest contrasts between block-level elements and inline ones is their handling of margins. 

- Inline boxes *completely ignore* the top and bottom margins of an element.

The rationale behind this goes back to the fact that inline boxes format runs of text inside of a block, and thus have limited impact on the overall layout of a page.

### Vertical Margin Collapse

- When you have two boxes with vertical margins sitting right next to each other, they will collapse. 
- Instead of adding the margins together,only the biggest one is displayed.

```css
p {
  padding: 20px 0 20px 10px;

  margin-top: 25px;
  margin-bottom: 50px;
}
```

- Each paragraph should have 50 pixels on the bottom, and 25 pixels on the top. That’s 75 pixels between our `<p>` elements, right? Wrong! There's still only going to be `50px` between them because the smaller top margin collapses into the bigger bottom one.

  ![margin-collapse](images/vertical-margin-collapse.png)

- To prevent the margins from collapsing. All you need to do is put another invisible element in between them:

```css
<p>...</p>
<div></div>
<p>...</p>
```

- The Flexbox layout scheme doesn't have collapsing margins, so this isn't really even an issue for modern websites.

### Generic Boxes

- There are many times when we need a generic box purely for the sake of styling a web page. This is what `<div>` and `<span>` are for.
- Both `<div>` and `<span>` are “container” elements that don't have any affect on the semantic structure of an HTML document.
- They provide a hook for adding CSS styles to arbitrary sections of a web page.
  - Sometimes you need to add an invisible box to prevent a margin collapse
  - You want to group the first few paragraphs of an article into a synopsis with slightly different text formatting.
- `div` is for block level content
- `span` is for inline content

### Content Boxes and Border Boxes

- The `width` and `height` properties only define the size of a box's *content*.
- Its padding and border are both added *on top of* whatever explicit dimensions you set.
- This is the default behavior, this is called `content-box`
- CSS lets you change how the width of a box is calculated via the `box-sizing` property.

```css
 box-sizing: border-box; 
```

- This forces the actual width of the box to be `200px`—including padding and borders. Of course, this means that the content width is now determined automatically
- Using `border-box` for all your boxes is considered a best practice among modern web developers.

### Aligning Boxes

There are 3 methods for horizontally aligning block-level elements:

- `auto margins` for center alignment
- `floats` for left right alignment
- `flexbox` for complete control over alignment

### Centering With Auto-Margins

- When you set the left and right margin of a block-level element to `auto`, it will center the block in its parent element.

```css
div {
     margin: 20px auto; /* Vertical  Horizontal */
}
```

- This only works on blocks that have explicit widths defined on them.

### Reseting Styles

- Different browsers have different default styles for all of their HTML elements, making it difficult to create consistent stylesheets.
- It is a  good idea to override default styles to a predictable value using the “universal” CSS selector (`*`).

```css
*  {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

- This selector matches every HTML element, effectively resetting the `margin` and `padding` properties for our web page. 
- It also converted all our boxes to `border-box` - which is a best practice.

## CSS Selectors

- CSS selectors let us map a single CSS rule to a specific HTML element. 
- This makes it possible to *selectively* style individual elements while ignoring others.
- Types of selectors
  - type selector
  - class selector
  - descendant selector
  - pseudo-class selector
  - ID selector

### Class selectors

- Class selectors let you apply CSS styles to a specific HTML element.
- They let you differentiate between HTML elements of the same type
- Class selectors require two things:
  - A `class` attribute on the HTML element in question.
  - A matching CSS class selector in your stylesheet.

```html
<p class='synopsis'>CSS selectors let you <em>select</em> individual HTML
   elements in an HTML document. This is <strong>super</strong> useful.</p>
```



```css
.synopsis {
  color: #7E8184;        /* Light gray */
  font-style: italic;
}
```

- The same class can be applied to multiple elements in a single HTML document.
- The order of the `class` attribute in our HTML element has no effect on override behavior.
- When there's two conflicting properties in a CSS file, the last one is always the one that gets applied.

### Descendant Selectors

- They let you target only those elements that are *inside* of another element.

```css
.synopsis em {
  font-style: normal;
}
```

- Descendant selectors aren't limited to class selectors—you can combine any other group of selectors this way

- If we wanted to select only `<em>` elements inside of headings, we might use something like this:

  ```css
  h1 em {
    /* Some other styles */
  }
  ```

### Pseudo-classes

Pseudo-classes begin with a colon followed by the name of the desired class. The most common link pseudo-classes are as follows:

- `:link` – A link the user has never visited.
- `:visited` – A link the user has visited before.
- `:hover` – A link with the user’s mouse over it.
- `:active` – A link that’s being pressed down by a  mouse (or finger).

```css
a:link {
  color: blue;
  text-decoration: none;
}
a:visited {
  color: purple;
}
a:hover {
  color: aqua;
  text-decoration: underline;
}
a:active {
  color: red;
}
```

Pseudo-classes aren't just for styling text links—they can be applied to any kind of selector (not just type selectors).

## ID selectors

- You can only have *one* element with the same ID per page
- They require an `id` attribute on whatever HTML element you're trying to select.
- The corresponding CSS selector must begin with a hash sign (`#`) opposed to a dot.

```html
<a id='button-2' class='button' href='nowhere.html'>Button Two</a>

```

```css
#button-2 {
  color: #5D6063;  /* Dark gray */
}
```

### URL fragments

- `id` attributes need to be unique because they serve as the target for “URL fragments”
- Fragments are how you point the user to a specific part of a web page.

![](images/fragment.png)

```html
<!-- From the same page -->
<a href='#button-2'>Go to Button Two</a>

<!-- From a different page -->
<a href='selectors.html#button-2'>Go to Button Two</a>
```

## Specificity

-  All else being equal, rules are applied from top-to-bottom.
- Unfortunately, not all CSS selectors are created equal. 
-  The whole "order matters”concept only works when all your rules have the same specificity.
- Certain selectors will *always* override other ones, regardless of where they appear in the stylesheet.