# Exercise 2 hints

Note that for the purposes of this exercise, the term "**colour swatch**" is used to refer to these rectanglular elements with a colour and a hex colour code:

![colour swatch](https://gcdnb.pbrd.co/images/X9wWSWJ6WFlr.png?o=1)

which can be seen in the [demo solution](https://liam-web-demos.pages.dev/002_colour_palette_viewer/solution/) of this exercise.

Click any of the sections below to expand them.

## How can I make the colour swatches display side-by-side?
<details>
  <summary>Click to expand or collapse this section</summary>

  Each collection of colour swatches is contained within an instance of `<div class="swatches-container">`, e.g.:
  ```html
  <div class="swatches-container">
    <div class="swatch"><p>#003049</p></div>
    <div class="swatch"><p>#D62828</p></div>
    <div class="swatch"><p>#F77F00</p></div>
    <div class="swatch"><p>#FCBF49</p></div>
    <div class="swatch"><p>#EAE2B7</p></div>
  </div>
  ```

  By default, the swatches flow vertically from top to bottom. However, by setting `display: flex` on the `swatches-container` class, the child elements of `swatches-container` will by display side-by-side horizontally.

  ```css
  .swatches-container {
    display: flex;
  }
  ```

  When you set `display: flex` on a container, it automatically sets the `flex-direction` property to `row`. 
  
  Keep in mind that not all flex containers need to be rows; it's also possible to set `flex-direction` to `column` if needed.
</details>

## How can I make the colour codes (#XXXXXX) display at the bottom of the colour swatches?
<details>
  <summary>Click to expand or collapse this section</summary>

 Each colour swatch is an element like the one below, where the hex colour code is in a `<p>` tag, which itself is a child of the swatch container:
 ```html
  <div class="swatch">
    <p>#F77F00</p>
  </div>
  ```

  So, if we want to push the `<p>` tag, say, to the bottom of the `<div>` container, we can:
  - Make the `<div>` a **flex** column.
  - Position the `<div>`'s children at the end (i.e. bottom) of the column.

  To position elements at the *end* of a flex container, you can set `justify-content: flex-end`. Here's what your CSS might look like:
  ```css
  .swatch {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    
    /* we should also give the swatch some extra height*/
    height: 200px;
  }
  ``` 
</details>

## How can I make the colour swatches stretch to share the available horizontal space evenly?
<details>
  <summary>Click to expand or collapse this section</summary>

 Although this is simple to achieve, it's not necessarily obvious how to do it.

 Assuming you have already made the `.swatches-container` elements into flex containers, i.e.:
 ```css
  .swatches-container {
    display: flex;
  }
 ```

... then all that needs to be done is to give all the colour swatches the same `flex-grow` value:
```css
.swatch {
  /* ... your other css ... */
  flex-grow: 1;
}
```

Normally, children of a flex container (often referred to as "flex items") will only take up as much space as needed, as determined by the item's content. But by setting `flex-grow` on a flex item, it tells the element to *grow* if there is extra space within the container. The value of the `flex-grow` property (in this case `1`) specifies the growth ratio compared to other elements within the same container. In this case, by setting the ratio to `1` for all of the swatches in the container, each swatch will grow with the exact same proportions, thus filling the space evenly.

[Click here for more information about the `flex-grow` property.](https://devdocs.io/css/flex-grow)
</details>

## How can I add a horizontal gap between the colour swatches?
<details>
  <summary>Click to expand or collapse this section</summary>

  The [gap property for Flexbox](https://caniuse.com/flexbox-gap) used to have poor browser support, but is now widely supported. You can set the `gap` property on `.swatches-container` like this:

  ```css
  .swatches-container {
    /* ... your other css... */
    gap: 0.5rem;
  }
  ```

  This will make it so that each child of the container is separated by a gap of `0.5rem`.
</details>

## How can I make the layout responsive (i.e. make the colour swatches stack vertically instead of horizontally on smaller screens)?
<details>
  <summary>Click to expand or collapse this section</summary>

  This can be done with a media query. For example, to apply certain styles only if the window is up to `550px` wide, this media query would do the trick:

  ```css
  @media screen and (max-width: 550px) {

    /* PLACE STYLES THAT ONLY APPLY TO SMALL SCREENS HERE */

  }
  ```

  Here is a (limited) set of examples of CSS rules that you might apply for smaller screen sizes:

  ```css
  @media screen and (max-width: 550px) {

    /* Make the swatches display in a column layout  */
    .swatches-container {
      flex-direction: column;
      gap: 0;
    }

    /* Display hex colour code within the horizontal space of the swatch */
    .swatch {
      flex-direction: row;
    }

  }
  ```
</details>

## How on earth do I get those little circles behind the "Palette Planet" logo?
<details>
  <summary>Click to expand or collapse this section</summary>

  Overlaid on the main header of the page, there is a smaller blue circle and a larger red circle:

  ![palette planet logo](https://gcdnb.pbrd.co/images/3rsq92ikhfge.png?o=1)

  But in the HTML, there are no elements to explicitly create these circles:
  ```html
  <h1><span>Palette</span> <span>Planet</span></h1>
  ```

  How is this possible?

  Allow me to introduce you to one of my favourite features of CSS which can be used for creating decorative effects: the `::before` and `::after` "**pseudo-elements**".

  Essentially, every HTML element has two secret "bonus" elements which you can style independently to create neat (or [ridiculously cool](https://a.singlediv.com/)) cosmetic effects.
  
  - Take a look at these quick references: [`::before`](https://devdocs.io/css/::before) / [`::after`](https://devdocs.io/css/::after)
  - View [this deep-dive article](https://codersblock.com/blog/diving-into-the-before-and-after-pseudo-elements/) for much more info and many more examples.

  To get the desired result in our case, you will have to set the following CSS property on the `<h1>` element:
  ```css
  h1 {
    /* ... your other css ... */
    position: relative;
  }
  ```

  Setting `position: relative` will allow us to freely position the `::before` and `::after` pseudo-elements relative to the `<h1>`.

  We should then specify the following styles on the `::before` and `::after` pseudo-elements:
  ```css
  h1::before, h1::after {
    position: absolute;   /* positions the elements relative to the <h1>  */
    content: '';          /* needed to make the pseudo-element display */
    border-radius: 100%;  /* just there to make them into circles :) */
  }
  ```

  Then, we can set unique styles on the `::before` element and the `::after` element to get the desired result:

  ```css
  /* Smaller blue circle */
  h1::before {
    width: 100px;
    height: 100px;
    background-color: rgba(18, 167, 190, 0.09);
    border-radius: 100%;
    top: -40px;
    left: 15px;
  }

  /* Larger red circle */
  h1::after {
    width: 180px;
    height: 180px;
    background-color: rgba(228, 21, 14, 0.1);
    border-radius: 100%;
    top: -5px;
    right: -5px;
  }
  ```

  Note that the `top` / `right` / `bottom` / `left` properties can be used as shown to offset the position of a [positioned element](https://devdocs.io/css/position#:~:text=A-,positioned%20element,-is%20an%20element). For example, in this case, `left: 15px` is used to position the smaller circle `15px` inwards relative to the *left* edge of the `<h1>`'s container.
</details>

