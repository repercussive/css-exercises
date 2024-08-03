# Exercise #1: Recipe page

For this task, you'll be taking a recipe webpage and adding some style to it to implement a minimal design. Click on the links below to see demos of the before and after:

- [Before](https://liam-web-demos.pages.dev/001_recipe_page/)
- [After](https://liam-web-demos.pages.dev/001_recipe_page/solution/)

## What you need to know

- The "before" files for this task are provided for you in the folder `/001_recipe_page`.

- There are two CSS files: `default-styles.css` and `your-styles.css`, which have already been linked to the `index.html` file. 

  - `default-styles.css` contains import statements for the fonts needed on the page: *"Libre Baskerville"* (header font) and *"DM Sans"* (body font). This will allow you to reference these fonts from other parts of your CSS with the `font-family` attribute.

  - When completing this task, do not edit the `default-styles.css` file. Add your own styles in the `your-styles.css` file.

- **Modifying the structure of the `index.html` document is not recommended** nor necessary. However, you are free to add `id` / `class` attributes to any of the tags in order to facilitate styling.

  - Avoid inline styling within HTML with the `style` attribute. Instead, keep your CSS code contained within `your-styles.css`.

## Things to keep in mind

The page is designed to be presentable on all standard screen sizes. Open up the "[After](https://liam-web-demos.pages.dev/001_recipe_page/solution/)" demo and experiment with resizing the window. You will want to make sure your page is similarly flexible. *You don't need any fancy tricks (such as media queries) to make this possible.*

Also, the page has a couple small bits of interactive visual feedback, which you should try to implement. For example, if you hover your mouse over any of the navigation links at the top of the page ("Home" / "Recipes" / "Contact"), they change colour.

## What if I get stuck? 

That's OK - the idea of these exercises is to expose you problems that you haven't seen before. That means you will encounter situations where you don't know what to do right away. In these situations, use the resources available to you, e.g.:

- Google liberally to find answers to questions. [(Example)](https://www.google.com/search?q=how+to+underline+text+css&oq=how+to+underline+text+css&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIMCAEQABgUGIcCGIAEMgcIAhAAGIAEMgcIAxAAGIAEMgcIBBAAGIAEMgcIBRAAGIAEMgcIBhAAGIAEMgcIBxAAGIAEMgYICBBFGDzSAQgxODY3ajBqMagCALACAA&sourceid=chrome&ie=UTF-8)

  -  Being a good developer is not about knowing or memorising everything. It's largely about knowing how to find information when you need it.

- Utilise references such as [devdocs.io](https://devdocs.io/).

- Inspect the "[After](https://liam-web-demos.pages.dev/001_recipe_page/solution/)" demo. You can right-click any element on the page and **Inspect** it. From the **Styles** tab of your developer tools, you can see all of the CSS rules that are applied to the element.

- Ask someone around you who might know the answer to your question.

- If none of the above lead you to the answer, there are a handful of hints provided in the `/hints` folder.

- And if that fails, there is an example solution provided in the `/solution` folder which you can study.