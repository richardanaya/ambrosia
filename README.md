# Ambrosia

A super simple single file semantic HTML css based off [Open Props UI](https://open-props-ui.netlify.app/). This project is really just an ultra easy way to utilize that project in HTMX applications.

* Simple theming
* Light/dark mode support

Check out the [demo](https://richardanaya.github.io/ambrosia/demo.html) of a wide variety of components.

<img width="465" alt="Screenshot 2025-04-20 at 12 01 32 PM" src="https://github.com/user-attachments/assets/cbed8267-164d-4f01-ad5d-61e1e98cdc80" />

# How to use

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/richardanaya/ambrosia/ambrosia.css" />
```

# Theming

Most people just need control over over the primary brand color, background, and border radius.

```css
@layer theme {
  html {
    color-scheme: var(--color-scheme);
  }

  .light {
    --color-scheme: light;
  }
  .dark {
    --color-scheme: dark;
  }

  :where(html) {
    color-scheme: light dark;

    --palette-hue: var(--oklch-green); /* Value: 1 - 360 of hugh colors. See color details below. */ 
    --palette-hue-rotate-by: 0; /* Should almost always be 0. See color details below. */
    --palette-chroma: 0.4; /* Saturation of colors (i.e. 0 = greyed out, 1 = full color. */

    --background: light-dark(var(--gray-1), var(--gray-12));

    --border-radius: var(--size-1);
    --field-border-radius: var(--size-1);
    --button-border-radius: var(--radius-round);
  }
}
```

## Color

Open Props UI uses 16 color css variables --color-1 through --color-16 based off the palette variables above. By default without hue rotation, you can think of these as light (1) to black(16). Chroma basically is saturation (whether your palette is greyed out or not). Rotation gives some variance than straight luminosity.

Check out this palette tool for advanced options or the [demo](https://richardanaya.github.io/ambrosia/demo.html)

https://opv2-beta.netlify.app/color/

Open props also has general color variables you can use:

* `--gray-1` - light grey
* `--red-10` - dark red

See more https://github.com/argyleink/open-props/blob/main/src/props.colors.css

## Advanced Theming

If you REALLY need to tweak every little detail, consider this. Otherwise, beyond this point you should look more deeply into Open Props UI and Open Props itself.

```css
@layer theme {
  html {
    color-scheme: var(--color-scheme);
  }

  .light {
    --color-scheme: light;
  }
  .dark {
    --color-scheme: dark;
  }

  :where(html) {
    color-scheme: light dark;

    --palette-hue: var(--oklch-green);
    --palette-hue-rotate-by: 0;
    --palette-chroma: 0.4;
    --background: light-dark(var(--gray-1), var(--gray-12));

    /* Borders */
    --border-radius: var(--size-1);

    /* Input Field */
    --field-border-radius: var(--size-1);

    /* Button */
    --button-border-radius: var(--radius-round);

    /* Advanced */

    /* Typography */
    --font-size-h1: var(--font-size-fluid-3, 3.5rem);
    --font-size-h2: var(--font-size-fluid-2, 2rem);
    --font-size-h3: var(--font-size-fluid-1, 1.5rem);
    --font-size-h4: var(--font-size-3, 1.25rem);
    --font-size-h5: var(--font-size-2, 1.1rem);
    --font-size-h6: var(--font-size-fluid-0, 1rem);
    --font-size-lg: var(--font-size-3, 1.25rem);
    --font-size-md: var(--font-size-fluid-0, 1rem);
    --font-size-sm: 0.875rem;
    --font-size-xs: var(--font-size-0, 0.75rem);


    /* Borders */
    --border-width: 1px;
    --field-border-color: var(--border-color);
    --border-color: light-dark(var(--gray-4), var(--gray-12));

    /* Primary */
    --primary: var(--color-8);
    --primary-light: oklch(from var(--primary) calc(l * 1.25) c h);
    --primary-dark: oklch(from var(--primary) calc(l * 0.75) c h);
    --primary-contrast: var(--gray-1);

    /* Text */
    --text-color-1: light-dark(var(--gray-15), var(--gray-1));
    --text-color-1-contrast: light-dark(var(--gray-2), var(--gray-15));
    --text-color-2: light-dark(var(--gray-13), var(--gray-4));
    --text-color-2-contrast: light-dark(var(--gray-4), var(--gray-13));

    /* Surface */
    --surface-default: light-dark(var(--gray-1), var(--gray-13));
    --surface-filled: light-dark(var(--gray-3), var(--gray-15));
    --surface-tonal: light-dark(var(--gray-3), var(--gray-12));
    --surface-elevated: light-dark(var(--gray-1), var(--gray-12));
  }
}
```


# Common open props

Since Ambrosia is based on open props, you have available to you a large number of props for things like spacing and size

```css
--size-1
--size-4
```

Check out https://open-props.style/ for more information!
