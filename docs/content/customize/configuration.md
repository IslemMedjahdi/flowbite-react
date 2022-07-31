---
layout: home
title: React Configuration - Flowbite
description: Learn how to customize the default Flowbite and Tailwind CSS options and styles
group: customize
toc: true

previous: Changelog
previousLink: getting-started/changelog/
next: Dark mode
nextLink: customize/dark-mode/
---

Before continuing, please make sure that you have installed Flowbite as a plugin inside your Tailwind CSS by following the [quickstart guide]({{< ref "getting-started/quickstart" >}}).

## Configuration file

You will probably want to be able to add your own colors, fonts, sizings, shadows, and other styles to the default set of utility classes from FlowBite and Tailwind CSS.

You can easily do that by editing the `tailwind.config.js` file from the root folder of your project.

```javascript
module.exports = {

  // add the folders and files from your templates
  content: ["./layouts/**/*.html", "./content/**/*.md", "./content/**/*.html", "./src/**/*.js"],

  // make sure to safelist these classes when using purge
  safelist: [
    'w-64',
    'w-1/2',
    'rounded-l-lg',
    'rounded-r-lg',
    'bg-gray-200',
    'grid-cols-4',
    'grid-cols-7',
    'h-6',
    'leading-6',
    'h-9',
    'leading-9',
    'shadow-lg'
  ],

  // enable dark mode via class strategy
  darkMode: 'class',

  theme: {
    extend: {
      // extend base Tailwind CSS utility classes
    }
  },
  plugins: [
    // include Flowbite as a plugin in your Tailwind CSS project
    require('flowbite/plugin')
  ]
}
```

## Theme

Use the `theme` object to define the color palette, fonts, border sizes, breakpoints. Basically, all of the visual design aspects of your website.

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    colors: {
      gray: colors.coolGray,
      blue: colors.lightBlue,
      red: colors.rose,
      pink: colors.fuchsia,
    },
    fontFamily: {
      sans: ['Graphik', 'sans-serif'],
      serif: ['Merriweather', 'serif'],
    },
    extend: {
      spacing: {
        '128': '32rem',
        '144': '36rem',
      },
      borderRadius: {
        '4xl': '2rem',
      }
    }
  }
}
```

## Variants

Use the `variants` object lets you define which variants (eg. hover, focus states) are used for each utility plugin.

```javascript
// tailwind.config.js
module.exports = {
  variants: {
    fill: [],
    extend: {
      borderColor: ['focus-visible'],
      opacity: ['disabled'],
    }
  },
}
```

## Plugins

The `plugins` object lets you define which external plugin you would like to include.

```javascript
// tailwind.config.js
module.exports = {
  plugins: [
    require('flowbite/plugin'),
    // ...
  ],
}
```

## Presets

Use the `presets` object to require another default set of configuration.

```javascript
// tailwind.config.js
module.exports = {
  presets: [
    require('@acmecorp/base-tailwind-config')
  ],

  // Project-specific customizations
  theme: {
    //...
  },
  // ...
}
```

## Prefix

You can use the `prefix` object to set a prefix for all of the classes generated by FlowBite and Tailwind CSS.

For example, you can add the `fb-` prefix like so:

```javascript
// tailwind.config.js
module.exports = {
  prefix: 'fb-',
}
```

Doing so it will add the prefix to all of the classes.

```css
.fb-text-left {
  text-align: left;
}
.fb-text-center {
  text-align: center;
}
.fb-text-right {
  text-align: right;
}
/* etc. */
```

If you'd like to browse the full list of configurable options, please visit the official <a href="https://tailwindcss.com/docs/configuration" rel="nofollow">Tailwind CSS configuration</a>.