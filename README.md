# Add TailwindCSS to VueJS

## Using Tailwind with Vue

### Step 1

First, I need to install the necessary packages.

```bash
npm install tailwindcss autoprefixer
```

#### Step 2

Now I create in assets a folder called `/styles` or `/css` and in that a file called `styles.css`. In this I write the following imports:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

#### Step 3

After that I am ready to import TailwindCSS into our project by adding this line in `main.js`.

```js
// src/main.js
import Vue from 'vue';
import App from './App.vue';

// Add this line
import './assets/styles/index.css';
```


