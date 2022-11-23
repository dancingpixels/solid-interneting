## Responsive Design

*Crafting mobile friendly websites*

- `RWD` is the idea that your website should display equally well in everything from widescreen monitors to mobile phones.
- Responsive design is accomplished through CSS media queries.
-  Media queries are a way to conditionally apply CSS rules. They tell the browser that it should ignore or apply certain rules depending on the user's device.

![](images/rwd.png)

- Media queries always begin with the `@media` “at-rule” followed by some kind of conditional statement, and then some curly braces. 
- Inside the curly braces, you put a bunch of ordinary CSS rules. 
- The browser only pays attention to those rules if the condition is met.

![](images/media-query-terms.png)

```css
/* Mobile Styles */
@media only screen and (max-width: 400px) {
  body {
    background-color: #F09A9D; /* Red */
  }
}
```

- The `only screen` media type means that the contained styles should only be applied to devices with screens (opposed to printed documents, like when you hit **Cmd+P** in a browser). 
- The `min-width` and `max-width` parts are called `media features`, and they specify the device dimensions you're targeting.

## Disabling Viewport Zooming

- Before responsive design was a thing, mobile devices only had a desktop layout to work with. 
- They zoomed out to fit the entire desktop layout into the width of the screen, letting the user interact with it by zooming in when necessary.
- This default behavior will prevent mobile devices from using  any mobile layout set by `@media` queries.
- To disable it, add the following element to the `<head>` of our document.

```html
<meta name='viewport'
      content='width=device-width, initial-scale=1.0, maximum-scale=1.0' />
```

