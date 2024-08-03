# Exercise 3 hints

Click any of the sections below to expand them.

## How can I make responsive grid layouts?
<details>
  <summary>Click to expand or collapse this section</summary>

  Both the **page header** and the **product cards section** use the *exact same CSS grid solution* to create a responsive layout. The layout is calculated *implicitly*.

  ![header grid](https://gcdnb.pbrd.co/images/kVTQlMknotqS.gif?o=1)

  Please have a full read through the "*Before you begin*" section of this exercise's `README` file to find more information about CSS grid, as well as links to resources which will help you create this type of layout. 

  If you are still stuck, here's an example of how the header section layout can be achieved:
  ```css
  header {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1rem;
  }
  ```
</details>

## How can I make the page accessible to keyboard users by adding focus styles?
<details>
  <summary>Click to expand or collapse this section</summary>

  Notice that the buttons on the page have a pink ring around them when tab-focused:

  ![keyboard focus example](https://gcdnb.pbrd.co/images/KyPojb9SrGci.gif?o=1)

  Adding this visual indicator is extremely important for accessibility.

  Historically, focus styles have been achieved by using the `:focus` pseudo-class, e.g.:

  ```css
  button:focus {
    outline: solid 2px red;
  }
  ```

  However, this would also apply the focus styles when a user *clicks* on a button with their mouse. This is generally redundant as mouse users don't typically need that visual feedback.

  In modern CSS, we now have the `:focus-visible` pseudo-class, which will only apply the focus styles if the browser deems it necessary. In practice, that generally means that the focus styles will only be applied if the user focuses on an element with their keyboard, and not with their mouse.

  We can use this to create the pink focus ring in this exercise.

  ```css
  *:focus-visible {
    outline: solid 6px rgb(239, 119, 169);
  }
  ```
</details>

## How can I make those animated buttons?
<details>
  <summary>Click to expand or collapse this section</summary>

  The buttons on the page:
  - Have a solid, green shadow behind them
  - Reach out when hovered
  - Depress when clicked

  ![Animation of hovering and pressing a button](https://gcdnb.pbrd.co/images/nIEXLO8MKXYv.gif?o=1)

  Let's start by making a class, `.animated-button`, to style the normal state of these buttons. See the CSS below. In particular, the `box-shadow` property is used to create the green shadow. `-5px` offsets the shadow 5 pixels to the left, and `5px` offsets the shadow 5 pixels down. *Tip: all Y-axis positioning in CSS assumes that the positive Y direction points downwards. That's why `+5px` means "5px down".*

  ```css
  .animated-button {
    box-shadow: -5px 5px rgb(59, 137, 59);
    border: solid 2px black;
    text-align: center;
    background-color: white;
    border-radius: 2px;
  }
  ```

  To make the button "reach out" when hovered, we need to add some `:hover` styles. In particular, we need to increase the size of the `box-shadow`. We also need to shift the `transform` position of the button slightly outwards to compensate for the increased size of the shadow.
  ```css
  .animated-button:hover {
    box-shadow: -8px 8px rgb(59, 137, 59);

    /* translate position 3px to the right, 3px up */
    transform: translate(3px, -3px);
  }
  ```

  To make the buttons depress when clicked, we need to add some [`:active` styles](https://devdocs.io/css/:active). Essentially, we want to do the opposite of what we just did above, i.e. reducing the size of the shadow, while moving the box slightly inwards.
  ```css
  .animated-button:active {
    box-shadow: -3px 3px var(--accent-color);

    /* translate position 2px to the left, 2px down */
    transform: translate(-2px, 2px);
  }
  ```

  Then, to make the animation smooth, we should add a `transition` to the `.animated-button` class.
  ```css
  .animated-button {
    /* ... your other CSS ... */
    transition: all 80ms;
  }
  ```

  Animating the `transform` of an element can result in ugly text aliasing issues on some browsers (e.g. Chrome & Edge on Windows). To resolve this, add the following property:
  ```css
  .animated-button {
    /* ... your other CSS ... */
    backface-visibility: hidden;
  }
  ```

  Finally, make sure that you apply the `animated-button` class attribute to your HTML elements as needed, e.g.:
  ```html 
  <header>
    <h1>seed theory</h1>
    <div>
      <p>...</p>

      <!-- add the animated-button class -->
      <a href="#" class="animated-button">Learn more</a>
    </div>
  </header>
  ```
</details>

## How can I configure the layout within the product cards?
<details>
  <summary>Click to expand or collapse this section</summary>

  If you have completed [CSS Grid Garden](https://cssgridgarden.com/), then you have covered everything you need to know in order to create this grid layout for the product cards:

  ![Grid example](https://gcdnb.pbrd.co/images/9fRhd1TbC276.png?o=1)

  If you're still stuck, let's walk through the basics of what we need to do.

  1. Make `.product` elements into `grid` containers.
  2. Configure the grid so that it contains 2 columns and 3 rows.
  3. Configure the grid items so that they sit within the correct rows and columns.

  Step 1: Make `.product` elements into `grid` containers:
  ```css
  .product {
    display: grid;
  }
  ```

  Step 2: Configure the grid so that it contains 2 columns and 3 rows:
  ```css
  .product {
    /* ... your other CSS ... */
    grid-template-columns: auto 1fr;
    grid-template-rows: auto 1.5fr 3fr;
  }
  ```

  In the case of `grid-template-columns`, we have created 2 columns. 
  - The leftmost column has a width of `auto`, which means the content within the column will determine the column's width. In practice, this means the column will be as wide as the product image element.
  - The rightmost column has a width of `1fr`, which in practice means the rightmost column will take up whatever remaining horizontal space exists within the grid container.

  In the case of `grid-template-rows`, we have created 3 rows.
  - The top row has a height of `auto`, which means the content within the row will determine the row's height. In practice, this means that the row will be as tall as the product title element.
  - The middle and bottom rows have a height of `1.5fr` and `3fr` respectively. 
    - This means that the middle row, which contains the product price element, will take up `1.5 / (1.5 + 3) = 33.3%` (one third) of the remaining vertical space within the grid container. 
    - The bottom row, which contains the "Add to cart" button, will take up `3 / (1.5 + 3) == 66.6%` (two thirds) of the remaining vertical space within the grid container.

  Step 3: Configure the grid items so that they sit within the correct rows and columns. For example, the "Add to cart" button needs to sit on the **2nd column** and the **3rd row**:
  ```css
  .product button {
    grid-column: 2;
    grid-row: 3;
  }
  ```

  Another example: the product image needs to sit on the **1st column**, but needs to **span across rows 2 and 3**:
  ```css
  .product-image-container {
    grid-column: 1;
    grid-row: 2 / span 2; /* start at row 2, span across 2 rows */
  }
  ```

  You can apply the same process to the other elements within the product card:
  - Product title (1st row, spans 2 columns)
  - Product price (2nd row, 2nd column)

  And then you'll have your grid layout sorted.

  ---

  *Side note - you may also want to limit the size of the product image if it's too big:*
  ```css
  .product-image-container {
    /* ... your other CSS ... */
    width: 8rem;
  }

  .product-image-container img {
    height: 100%;
    width: 100%;
  }
  ```
</details>

## How can I make the product images "stick out" like that?
<details>
  <summary>Click to expand or collapse this section</summary>

  Notice that the images on the product cards stick out slightly past the left of their container. There is also a small decorative element (it's just a black triangle) that creates the impression that the image has been "folded around" the product card.

  ![product card with folded corner highlighted](https://gcdnb.pbrd.co/images/BkTMg19pUZWN.png?o=1)

  Making the image stick out to the left is relatively simple, using the `transform` property:

  ```css
  .product-image-container {
    transform: translateX(-1.5rem);
  }
  ```

  Adding the black triangle is a little more involved. We can achieve it using the `::before` or `::after` pseudo-element.

  **If you need a refresher on pseudo-elements, please open the hints for Exercise 2 and view the section titled "How on earth do I get those little circles behind the "Palette Planet" logo?"** 

  For this task, we will create a pseudo-element which is pinned near the top-left corner of the product image.

  To do this, we first need to set `position: relative` on the product image container:
  ```css
  .product-image-container {
    position: relative;
  }
  ```

  Then add the `::before` pseudo-element (with a separate selector):
  ```css
  .product-image-container::before {
    position: absolute;
    content: '';
    width: 0.5rem;
    height: 0.5rem;
    top: calc(-0.5rem - 1px);
    left: -2px;
    background-color: black;
  }
  ```

  This will create a black square near the top-left corner of the image:

  ![progress image](https://gcdnb.pbrd.co/images/ifC9dz2uXCC0.png?o=1)

  To make it triangular, we can use the `clip-path` property. For situations like this, you can use [this CSS clip path maker](https://bennettfeely.com/clippy/). By drawing a right-angled triangle, you get a `clip-path` that looks something like this:
  ```css
  .product-image-container::before {
    /* ... your other CSS ... */
    clip-path: polygon(100% 25%, 0% 100%, 100% 100%);
  } 
  ```

  ... which creates the shape we're looking for.

  **Note:** `::before` and `::after` pseudo-elements only work when attached to HTML elements that can contain children. `<img>` elements cannot contain children, so `::before` / `::after` will not work on them. That is why the product images have been placed inside of the `.product-image-container` `<div>`s. That allows us to attach the pseudo-elements to the `<div>` container, rather than the image itself.

</details>

## How can I make those little green triangles near the "seed theory" logo?
<details>
  <summary>Click to expand or collapse this section</summary>

  In the final product, there are two translucent green triangles pinned to the bottom-right of the `<h1>` element, creating a sort of "mountain range" impression.

  ![page header](https://gcdnb.pbrd.co/images/aNBk04qvmAua.png?o=1)

  This has been achieved using `::before` and `::after` pseudo-elements. **If you need a refresher on pseudo-elements, please open the hints for Exercise 2 and view the section titled "How on earth do I get those little circles behind the "Palette Planet" logo?"** 

  If you are still unsure how to approach this, let's walk through it.

  First, we'll have to set `position: relative` on the `<h1>` element:
  ```css
  h1 {
    /* ... your other CSS ... */
    position: relative;
  }
  ```

  Then, we'll set key rules for the `::before` and `::after` pseudo-selectors:
  ```css
  h1::before, h1::after {
    position: absolute;
    background-color: rgb(59, 137, 59);
    content: '';
    opacity: 0.22;
  }
  ```

  Then, we can set the position and dimensions of the pseudo-elements:
  ```css
  h1::before {
    width: 4.5rem;
    height: 4.5rem;
    bottom: 0;
    right: 0;
  }

  h1::after {
    width: 6rem;
    height: 6rem;
    bottom: 0;
    right: 2rem;
  }
  ```

  This will create two rectangular elements:

  ![progress image](https://gcdnb.pbrd.co/images/00CPsLoWBgfR.png?o=1)

  To make them triangular, you can use the `clip-path` property. Using [this `clip-path` maker](https://bennettfeely.com/clippy/), draw the desired triangle shape. Take the CSS code output and apply it to the pseudo-elements:

  ```css
  h1::before, h1::after {
    /* ... your other CSS ... */
    clip-path: polygon(100% 100%, 50% 50%, 0 100%);
  }
  ```

  This should give us the result we want.

  ![result](https://gcdnb.pbrd.co/images/zSgN9zO3gZwD.png?o=1)


</details>

