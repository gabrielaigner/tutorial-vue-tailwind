# Add TailwindCSS to VueJS

#### Step 1

First, I need to install the necessary packages.

```bash
npm install tailwindcss autoprefixer
```

**Step 2** *(optional, it's for configuration)*

To customize my Tailwind installation, I create the `tailwind.config.js` with the command:

```bash
npx tailwind init
```

This will create a minimal `tailwind.config.js` file in my project:

```js
// tailwind.config.js
module.exports = {
  theme: {},
  variants: {},
  plugins: [],
}
```

More about *configuring* Tailwind is in the [configuration documentation](https://tailwindcss.com/docs/configuration/).

#### Step 3

Now I create in assets a folder called `/styles` or `/css` and in that a file called `styles.css`. In this I write the following imports:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```
