![Ergonomize.css v4.0](https://www.ergonomizecss.com/assets/medias/images/ergonomizecss-banner-doc-github-big.webp)

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

## Selection

This part removes a possible default shadow of text during a selection, making the text unreadable according to the background color of the selected text.

```css
/**
 * 1. For Firefox 2+, Firefox for Android 33+.
 * 2. For Chrome 4+, Safari 3.1+, Opera 9.6+, Android 4.4+.
 */

::-moz-selection {
    background: #b3d4fc;
    color: #fff;
    text-shadow: none; /* 1 */
}

::selection {
    background: #b3d4fc;
    color: #fff;
    text-shadow: none; /* 2 */
}
```

These selection rule sets have to be separate and the `background` property must be defined when declaring `::selection` in a CSS file. Feel free to adapt `background` and `color` values to your project.

* [Bug fix source: Mike Taylor](https://twitter.com/miketaylr/status/12228805301)
* [::selection browsers support](https://caniuse.com/#feat=css-selection)

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
/**
 * 1. For some Firefox.
 */

html {
    overflow-y: scroll;
    overflow: -moz-scrollbars-vertical; /* 1 */
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

## Grouping content

Prevents `blockquote` and `pre` content from spilling their container.

```css
blockquote,
pre {
    max-width: 100%;
}
```

Adds a better looking default horizontal rule.

```css
hr {
    border: 0;
    border-top: 1px solid #ccc;
    display: block;
    height: 1px;
    margin: 1em 0;
    padding: 0;
}
```

## Text-level semantics

Removes delay from tapping on links and removes gaps in links underline in iOS 8+ and Safari 8+.

```css
a {
    -ms-touch-action: manipulation;
        touch-action: manipulation;
    -webkit-text-decoration-skip: objects; /* 2 */
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

## Embedded content

Removes delay from tapping on `area`.

```css
area {
    -ms-touch-action: manipulation;
     touch-action: manipulation;
}
```

* [Click delay mobile devices trick source](https://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/)

Removes the gap between `audio`, `canvas`, `iframe`, `image`, `video` elements and the bottom of their container.

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

* [Remove gap embedded content trick source](https://github.com/h5bp/html5-boilerplate/issues/440)

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

Changes the fill color to match the text color in all browsers.

```css
svg {
    fill: currentColor;
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
    -ms-touch-action: manipulation;
        touch-action: manipulation;
}
```

* [Click delay mobile devices trick source](https://www.sitepoint.com/5-ways-prevent-300ms-click-delay-mobile-devices/)

Fixes vertical align for form elements.

```css
button,
input,
label,
select {
    vertical-align: middle;
}
```

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