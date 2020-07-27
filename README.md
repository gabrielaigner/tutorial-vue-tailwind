# Add TailwindCSS to VueJS

## Using Tailwind with Vue

### Step 1

First, I need to install the necessary packages.

```bash
npm install tailwindcss autoprefixer
```

### Step 2

After installing `TailwindCSS` as a dependency of my project I add it to the list of Post CSS plugins inside the `postcss.config.js` file. Now it's in my build chain.

```js
// postcss.config.js
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer'),
  ],
}
```

#### Step 3

Now I create in assets a folder called `/styles` or `/css` and in that a file called `style.css`. In this I write the following imports:

```css
/* src/assets/styles/style.css */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

#### Step 4

After that I am ready to import TailwindCSS into our project by adding this line in `main.js`.

```js
// src/main.js
import Vue from 'vue';
import App from './App.vue';

// Add this line
import './assets/styles/style.css';
```

## Customizing the Tailwind configuration

### Step 5

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

## Optimize bundle-size with PurgeCSS

By default tailwindcss is very big and has more than `600 KB`.

### Step 6

To remove the not used CSS-Classes I use `PurgeCSS`. I install the necessary package:

```bash
npm install purgecss  @fullhuman/postcss-purgecss
```

After installing the `postcss-purgecss plugin`, I must add it to my `postcss.config.js`.

```js
// postcss.config.js
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('autoprefixer'),

    // Only uses purgecss in production
    process.env.NODE_ENV === 'production' && require('@fullhuman/postcss-purgecss')({
      content: [
        './src/**/*.html',
        './src/**/*.vue'
      ],
      defaultExtractor: content => content.match(/[A-Za-z0-9-_:/]+/g) || []
    })
  ],
}
```

I now run `npm run build` and the bundle-size should be tiny.
