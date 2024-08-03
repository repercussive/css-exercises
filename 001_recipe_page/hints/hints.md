# Exercise 1 hints

Click any of the sections below to expand them.

## How can I set the right fonts?
<details>
  <summary>Click to expand or collapse this section</summary>

  The fonts you need for this exercises are already imported for you in `default-styles.css`, however you still need to set the appropriate fonts from your own CSS.

  The body font is `DM Sans`, which you can set like this:
  ```css
  body {
    font-family: 'DM Sans', sans-serif;
  }
  ```

  Note that `sans-serif` is specified as a fallback font in case `DM Sans` could not be loaded by the user's browser.

  For headers, the font is `Libre Baskerville`, which you can set like this:
  ```css
  h1, h2, h3, h4, h5, h6 {
    font-family: 'Libre Baskerville', serif;
  }
  ```

  The website title "*Delicioso*" at the top of the page also needs the `Libre Baskerville` font, and must be set to display in italics. The element is an `<a>` tag which resides inside the `<header>` tag. You can style it like this:
  ```css
  header a {
    font-family: 'Libre Baskerville', serif;
    font-style: italic;
    font-weight: 500;
  }
  ```
</details>

## How can I horizontally centre the main content of the page?
<details>
  <summary>Click to expand or collapse this section</summary>

  In the [final product](https://liam-web-demos.pages.dev/001_recipe_page/solution/), the main content of the page - represented by the `<main>` tag - is mostly left-aligned (such as the text in the "Ingredients" section), but the text container itself has an equal amount of spacing on the left and right sides.

  ![page margin diagram](https://gcdnb.pbrd.co/images/JhDgCGy9x23l.png?o=1)

  To achieve this:

  - The content container (`<main>`) must have a **maximum width** to prevent the content from stretching across the entire screen.

    - This can be done by setting the `max-width` attribute on the `main` element. 

  - The content container must have **equal margin** space on the left and right sides.

    - One way to achieve this is by setting `margin: auto` on the `main` element. This means that whatever horizontal space is available will be evenly distributed on either side of the `main` element. 

  Here is a code example:

  ```css
  main {
    max-width: 800px;
    margin: auto;
  }
  ```

  To prevent the content from being crammed into the sides on smaller screens, you can add some padding: 

  ```css
  main {
    padding-left: 0.75rem;
    padding-right: 0.75rem;
  }
  ```
  You can use `margin: auto` any time you want to horizontally centre some content within its container. Note that this does not work for vertical centering; for that you will have to rely on other features such *flexbox* or *grid*.

</details>

## How can I animate the navigation links when hovering the mouse over them?
<details>
  <summary>Click to expand or collapse this section</summary>

  The background colour of the navigation links ("Home" / "Recipes" / "Contact") changes on mouse hover. 
  
  You can achieve hover styles with the `:hover` *"pseudo-class"*.

  First, I recommend adding an `id` attribute to the `<div>` which contains the navigation links, e.g.:
  ```html
  <div id="nav-links-container">
    <a href="#">Home</a>
    <a href="#">Recipes</a>
    <a href="#">Contact</a>
  </div>
  ```

  This will allow you to easily apply the same styles to all of the links, e.g.:
  ```css
  #nav-links-container a {
    padding: 0.3rem 1rem;
    margin-inline: 0.05rem;
    border-radius: 2px;
    color: rgb(77, 77, 77);
  }
  ```

  **Separately from the selector shown above**, you can now add a new selector which specifies the styles to apply on hover. This new selector should include the `:hover` pseudo-class:
  ```css
  #nav-links-container a:hover {
    background-color: rgba(100, 148, 237, 0.245);
    color: black;
  }
  ```

  If you want the `color` and/or `background-color` property to transition smoothly rather than changing instantaneously, you can specify this using the `transition` property:
  ```css
  #nav-links-container a {
    transition: background-color 100ms, color 100ms;

    /*  ... your other css ... */
  }
  ```

  This means that any time the `background-color` or `color` properties change, the value will transition smoothly over a time period of 100 milliseconds.
</details>

## How can I position the elements within the footer?
<details>
  <summary>Click to expand or collapse this section</summary>

  The `<footer>` element at the bottom of the page contains two direct children: a `<div>` containing a few social links, and a `<p>` tag detailing the website's license. [As in the final product](https://liam-web-demos.pages.dev/001_recipe_page/solution/), the `<p>` tag should be aligned to the right side of the container.

  My preferred way to achieve this is with **flexbox**, which is an extremely useful and powerful feature of CSS. You can learn about flexbox with [this interactive game](https://flexboxfroggy.com/).

  Flexbox allows us to easily position the elements of the footer, like this:
  ```css
  footer {
    display: flex;
    justify-content: space-between; /* maximises the horizontal space between the <footer>'s children. */
  }
  ```
</details>