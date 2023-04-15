![Ergonomize.css v4.2](https://www.ergonomizecss.com/assets/medias/images/ergonomizecss-banner-doc-github-big.webp)

# Documentation

Ergonomize.css is a CSS file aiming at bringing additional rules to HTML elements without altering their default styles in order to improve the user experience.

* [The project Website](https://www.ergonomizecss.com/)

## Scroll Behavior

If the user has not requested the system to minimize the amount  of animation or movement, Defines a smooth scroll effect to the scrolling behavior for a scrolling box, when scrolling happens due to navigation or CSSOM scrolling APIs.

```css
@media (prefers-reduced-motion: no-preference) {
    :root {
        scroll-behavior: smooth; 
    }
}
```

## The root element

Improve consistency of default fonts in all browsers (often more readable than the default `serif` typo).

```css
html {
    font-family: system-ui, 
                'Segoe UI', 
                 Roboto, 
                 Helvetica, 
                 Arial, 
                 sans-serif, 
                'Apple Color Emoji', 
                'Segoe UI Emoji';
}
```

Forces scrollbars to always be visible to prevent awkward jumps when navigating between pages that do/do not have enough content to produce scrollbars naturally.

```css

html {
    overflow-y: scroll;
}
```

Displays auto-hiding scrollbars during mouse interactions and panning indicators during touch and keyboard interactions.

```css
html {
    -ms-overflow-style: -ms-autohiding-scrollbar;
}
```

Fonts on OSX will look more consistent with other systems that do not render text using sub-pixel anti-aliasing.

```css
html {
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
}
```

Removes the highlighting effect of “tap” actions on WebKit.

```css
/**
 * 1. For Androids.
 * 2. For some Androids.
 */ 

html {
    -webkit-tap-highlight-color: rgba(0,0,0,0); /* 1 */
    -webkit-tap-highlight-color: transparent; /* 2 */
}
```

* [Trick source](https://phonegap-tips.com/articles/essential-phonegap-css-webkit-tap-highlight-color.html)

Prevents iOS text size adjust after orientation change, without disabling user zoom.

```css
html {
    -webkit-text-size-adjust: 100%;
}
```

Forces scrollbars to always be visible to prevent awkward jumps when navigating between pages that do/do not have enough content to produce scrollbars naturally.

```css
html {
  tab-size: 4;
  -moz-tab-size: 4;
}
```

## Grouping content

Prevents `blockquote` and `pre` content from spilling their container.

```css
blockquote,
pre {
    max-width: 100%;
}
```

Improve consistency of default fonts in all browsers.

```css
pre {
    font-family: ui-monospace, 
                 SFMono-Regular, 
                 Consolas, 
                 'Liberation Mono', 
                 Menlo, 
                 monospace;
}
```

## Text-level semantics

Use a more readable tab size.

```css
a {
    touch-action: manipulation;
    -webkit-text-decoration-skip: objects;
}
```

* [Click delay mobile devices trick source](https://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/)

Gives a help cursor to elements that give extra info on `:hover`.

```css
abbr[title],
dfn[title] {
    cursor: help;
}
```

Display for `code` the text as it was written and line breaks so that text does not leave the block and prevents `code` content from spilling their container.

```css
code {
    white-space: pre-wrap;
    max-width: 100%;
}
```

Improve consistency of default fonts in all browsers.

```css
code,
kbd,
samp {
    font-family: ui-monospace, 
                 SFMono-Regular, 
                 Consolas, 
                 'Liberation Mono', 
                 Menlo, 
                 monospace;
}
```

## Embedded content

Removes delay from tapping on `area`.

```css
area {
    touch-action: manipulation;
}
```

* [Click delay mobile devices trick source](https://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/)

Remove the gap between audio, canvas, iframes, images, videos and the bottom of their containers.

```css
audio,
canvas,
iframe,
img,
svg,
video {
    vertical-align: middle;
}
```

Preserves the aspect ratio on image.

```css
img {
    height: auto;
}
```

Disables highlight on image when selecting and dragging it with the mouse.

```css
/**
 * 1. For Firefox 2+, Firefox for Android 33+.
 * 2. For Chrome 4+, Safari 3.1+, Opera 9.6+, Android 4.4+.
 */

img::-moz-selection { /* 1 */
    background-color: transparent;
}

img::selection { /* 2 */
    background-color: transparent;
}
```

* [Disable highlight on image trick source](https://stackoverflow.com/questions/6816080/how-to-disable-highlight-on-a-image)

Prevents `img`, `svg` and `video` content from spilling their container.

```css
img,
svg,
video {
    max-width: 100%;
}
```

## Forms

Gives a pointer cursor to clickable forms elements.

```css
[type=button]:not(:disabled),
[type=reset]:not(:disabled),
[type=submit]:not(:disabled),
button:not(:disabled),
label[for],
select {
    cursor: pointer;
}
```

Removes delay from tapping on `button`, `input`, `label`, `select` and `textarea` elements.

```css
button,
input,
label,
select,
textarea {
    touch-action: manipulation;
}
```

* [Click delay mobile devices trick source](https://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/)

Prevents `input` and `textarea` content from spilling their container.

```css
input,
textarea {
    max-width: 100%;
}
```

Allows only vertical resizing of `textarea`.

```css
textarea {
    resize: vertical;
}
```

## Tables

Prevents `table` and `td` content from spilling their container.

```css
table,
td {
    max-width: 100%;
}
```