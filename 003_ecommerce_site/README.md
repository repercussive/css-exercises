# Exercise #3: E-commerce site

In this exercise, you'll take the concept of a responsive layout to the next level. Click on the links below to see demos of the before and after:

- [Before](https://liam-web-demos.pages.dev/003_ecommerce_site/)
- [After](https://liam-web-demos.pages.dev/003_ecommerce_site/solution/)

This time around, the design of the page is loosely inspired by a sort of softer take on neo-brutalism.

Experiment with resizing the window to see how the page adapts.

## What you need to know

- ⚠️ For this task, you ***should not use any media queries***. Instead, rely on the responsive power of CSS Grid. See more details in the section titled "Before you begin" below.  

- The "before" files for this task are provided for you in the folder `/003_ecommerce_site`.

- There are two CSS files: `default-styles.css` and `your-styles.css`, which have already been linked to the `index.html` file. 

  - `default-styles.css` contains import statements for the single font needed on the page: *"Inter"*.

  - When completing this task, do not edit the `default-styles.css` file. Add your own styles in the `your-styles.css` file.

- **Modifying the structure of the `index.html` document is not recommended** nor necessary. However, you are free to add `id` / `class` attributes to any of the tags in order to facilitate styling.

  - Avoid inline styling within HTML with the `style` attribute. Instead, keep your CSS code contained within `your-styles.css`.

## Before you begin

To complete this task, you will need to understand the fundamentals of **CSS Grid**, an extremely flexible feature of CSS that allows you to make responsive 2-dimensional layouts. 

A good place to start learning about CSS grid is with [CSS Grid Garden](https://cssgridgarden.com/).

If you want to improve your understanding, I recommend watching [this video](https://www.youtube.com/watch?v=rg7Fvvl3taU) as well.

This will prepare you to start creating **explicit** grid layouts, i.e. ones where you manually define the dimensions and areas of the grid. A good example of an explicit grid in this exercise could be the product cards:

![Product card](https://gcdnb.pbrd.co/images/B9dTbLzAQVkm.png?o=1)

To create this layout, you could define the rows and columns of the grid like this:

![Grid example](https://gcdnb.pbrd.co/images/9fRhd1TbC276.png?o=1)

But that's not all! To complete this task, you will also need to be able to create **implicit** grids. This is where you don't actually specify all the details of the grid, but instead specify some *rules* about how the grid is supposed to work, then allow the browser to calculate the result on the fly.

A good example of an implicit grid in this exercise would be the grid of product cards:

![Responsive grid of product cards](https://gcdnb.pbrd.co/images/zossXuFWLGrV.gif?o=1)

Notice that the grid is able to adapt to any screen size. This is made possible by setting these rules:
1. The maximum width of the entire grid container is 1050 pixels.
2. The minimum width of each grid column is 300 pixels, and the maximum width of each column is `1fr` (more on `fr` below!)
3. The number of columns in the grid should be automatically calculated as *the maximum number of columns that can exist while still satisfying rules 1 and 2.*

Some resources to help you learn about implicit grids:
- Here is a [live working example](https://gridbyexample.com/examples/example28/) of exactly the kind of thing I've described above. If you want to view the example as a resizable full page, [click here](https://gridbyexample.com/examples/code/example28).
- Here is a [YouTube video](https://www.youtube.com/watch?v=mVQiNpqXov8) on using the `minmax()` function, which is what makes this possible.
- If you aren't sure about `fr` units, [watch this video](https://www.youtube.com/watch?v=ZPtpzuRajzM) which I think does a good job of making it clear how `fr` functions and why it's useful.

💡 Tip: you can use the same concept of implicit grids for the site's header :)

## Important note on accessibility

It should be possible to navigate any website **without the use of a mouse**. Keyboard navigation should therefore provide a good, usable experience. 

Normally, users who rely on keyboard navigation will use the **Tab** key to focus on the different elements on the page. It is absolutely vital that there is a good visual indicator of which element is currently focused. 

Given the design of this website, the default visual focus indicator of some browsers is nearly impossible to see. Therefore, it is your responsibility to use CSS to make the focus indicator easily identifiable. Open the "[After](https://liam-web-demos.pages.dev/003_ecommerce_site/solution/)" demo and try pressing the Tab key a few times to test out the keyboard navigation. You should see a large, pink focus ring appear around the focused elements. This provides more contrast and clarity than the browser's default focus ring.

You can use the [`:focus-visible` pseudo-class](https://devdocs.io/css/:focus-visible) in CSS to apply focus styles for keyboard users.

## One more super tip

The final product has some slightly funky buttons that move when hovered/pressed:

![Animation of hovering and pressing a button](https://gcdnb.pbrd.co/images/nIEXLO8MKXYv.gif?o=1)

If you are planning on stealing the CSS for this from the "[After](https://liam-web-demos.pages.dev/003_ecommerce_site/solution/)" demo (which is a fine idea), or you just want to debug your own CSS hover styles, you'll want to know this tip: when you right-click on an element and press **Inspect**, in the Styles tab of your developer tools you'll find a button labelled "**Toggle Element State**". Here's what it looks like in Edge:

!["Toggle Element State" button in Edge developer tools](https://gcdnb.pbrd.co/images/owjaBoTqAW4y.png?o=1)

When you click that, you'll then see a menu which allows you to toggle element states like hover, press, and keyboard focus, and will display the CSS rules associated with those states.

## What if I get stuck? 

That's OK - the idea of these exercises is to expose you problems that you haven't seen before. That means you will encounter situations where you don't know what to do right away. In these situations, use the resources available to you, e.g.:

- Google liberally to find answers to questions. [(Example)](https://www.google.com/search?q=how+to+underline+text+css&oq=how+to+underline+text+css&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIMCAEQABgUGIcCGIAEMgcIAhAAGIAEMgcIAxAAGIAEMgcIBBAAGIAEMgcIBRAAGIAEMgcIBhAAGIAEMgcIBxAAGIAEMgYICBBFGDzSAQgxODY3ajBqMagCALACAA&sourceid=chrome&ie=UTF-8)

  -  Being a good developer is not about knowing or memorising everything. It's largely about knowing how to find information when you need it.

- Utilise references such as [devdocs.io](https://devdocs.io/).

- Inspect the "[After](https://liam-web-demos.pages.dev/003_ecommerce_site/solution/)" demo. You can right-click any element on the page and **Inspect** it. From the **Styles** tab of your developer tools, you can see all of the CSS rules that are applied to the element.

- Ask someone around you who might know the answer to your question.

- If none of the above lead you to the answer, there are a handful of hints provided in the `/hints` folder.

- And if that fails, there is an example solution provided in the `/solution` folder which you can study.
