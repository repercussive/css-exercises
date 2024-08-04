# Exercise #2: Colour palette viewer

For this task, you'll be using CSS to handle both style and layout. Click on the links below to see demos of the before and after:

- [Before](https://liam-web-demos.pages.dev/002_colour_palette_viewer/)
- [After](https://liam-web-demos.pages.dev/002_colour_palette_viewer/solution/)

This time around, you'll be creating a responsive layout. See the section titled "Before you begin" below for more details.

## What you need to know

- The "before" files for this task are provided for you in the folder `/002_colour_palette_viewer`.

- There are two CSS files: `default-styles.css` and `your-styles.css`, which have already been linked to the `index.html` file. 

  - `default-styles.css` contains import statements for the fonts needed on the page: *"Dancing Script"* (header font) and *"Inter"* (body font). This will allow you to reference these fonts from other parts of your CSS with the `font-family` attribute.

  - When completing this task, do not edit the `default-styles.css` file. Add your own styles in the `your-styles.css` file.

- **Modifying the structure of the `index.html` document is not recommended** nor necessary. However, you are free to add `id` / `class` attributes to any of the tags in order to facilitate styling.

  - Avoid inline styling within HTML with the `style` attribute. Instead, keep your CSS code contained within `your-styles.css`.

## Before you begin

The page is designed to be **responsive** so that it displays nicely on screens of any size. Notice that the width of the colour swatches adapts to the screen size, and that at a certain point the layout "snaps" and changes completely.

![Example animation of resizing the window](https://gcdnb.pbrd.co/images/GRZcPcjW8qeD.gif?o=1)

You'll have to configure the CSS so that the colour swatches fit within the width of the screen - and, if the screen is too narrow, change it so that the colour swatches display in rows instead of columns, as shown above.

For layout, I highly recommend taking a deeper look into **flexbox** if you haven't done so already.
- [Flexbox froggy, an interactive game for learning flexbox](https://flexboxfroggy.com/)
- [An interactive guide to flexbox](https://www.joshwcomeau.com/css/interactive-guide-to-flexbox/)

For shifting the layout on narrow screens, this can be achieved with the help of a **media query**.
- [Guide to media queries](https://css-tricks.com/a-complete-guide-to-css-media-queries/)
- [w3schools example](https://www.w3schools.com/cssref/tryit.php?filename=trycss3_media_bg)

## What if I get stuck? 

That's OK - the idea of these exercises is to expose you problems that you haven't seen before. That means you will encounter situations where you don't know what to do right away. In these situations, use the resources available to you, e.g.:

- Google liberally to find answers to questions. [(Example)](https://www.google.com/search?q=how+to+underline+text+css&oq=how+to+underline+text+css&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIMCAEQABgUGIcCGIAEMgcIAhAAGIAEMgcIAxAAGIAEMgcIBBAAGIAEMgcIBRAAGIAEMgcIBhAAGIAEMgcIBxAAGIAEMgYICBBFGDzSAQgxODY3ajBqMagCALACAA&sourceid=chrome&ie=UTF-8)

  -  Being a good developer is not about knowing or memorising everything. It's largely about knowing how to find information when you need it.

- Utilise references such as [devdocs.io](https://devdocs.io/).

- Inspect the "[After](https://liam-web-demos.pages.dev/002_colour_palette_viewer/solution/)" demo. You can right-click any element on the page and **Inspect** it. From the **Styles** tab of your developer tools, you can see all of the CSS rules that are applied to the element.

- Ask someone around you who might know the answer to your question.

- If none of the above lead you to the answer, there are a handful of hints provided in the `/hints` folder.

- And if that fails, there is an example solution provided in the `/solution` folder which you can study.
