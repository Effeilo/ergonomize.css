![Ergonomize.css v2.0.0](http://www.ergonomizecss.com/ergonomizecss-tall-compressor.png)

# Documentation

Ergonomize.css is a CSS file aiming at bringing additional rules to HTML elements without altering their default styles in order to improve the user experience.

* [The project Website](http://www.ergonomizecss.com/)

## Viewport

Using `device-width` improves user experience on mobile devices and tablets. We currently use a meta tag:

```html
<meta name="viewport" content="width=device-width">
```

This module incorporates the basic principles of meta viewport while respecting the CSS standards.

`@viewport` is very little supported by browsers at the moment, it remains however useful for Windows 8 Snap Mode, which does not support the meta viewport.

```css
/*
 * 1. For IE 10+, IE mobile 10+.
 * 2. For Opera mini 8.
 */

@-ms-viewport {
  width: device-width; /* 1 */
}

@-o-viewport {
  width: device-width; /* 2 */
}
```

This part fixes a bug for IE10 mobile on Lunia 920.

```css
@media screen and (max-width: 400px) {
  @-ms-viewport {
    width: 320px;
  }
}
```

* [Bug fix source: Tim Kadlec](https://timkadlec.com/2013/01/windows-phone-8-and-device-width/)
* [@viewport browsers support](http://caniuse.com/#feat=css-deviceadaptation)

## Selection

Removes a possible default text shadow during selection, making content unreadable depending on the background color of the selected text.

```css
/*
 * 1. For Firefox 2+, Firefox for Android 33+.
 * 2. For IE 9+, Chrome 4+, Safari 3.1+, Opera 9.6+, Android 4.4+, IE Mobile.
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
* [::selection browsers support](http://caniuse.com/#feat=css-selection)

## The root element

On screen, relying on `sans-serif` is often more readable than the default `serif` font face.

```css
html {
  font-family: sans-serif;
}
```

Forces scrollbars to always be visible to prevent awkward jumps when navigating between pages that do/do not have enough content to produce scrollbars naturally.

```css
/*
 * 1. For some Firefox.
 */

html {
  overflow-y: scroll;
  overflow: -moz-scrollbars-vertical; /* 1 */
}
```

* [Force scrollbars trick source](https://css-tricks.com/snippets/css/force-vertical-scrollbar/)

Defines a smooth scroll effect to the scrolling behavior for a scrolling box, when scrolling happens due to navigation or CSSOM scrolling APIs.

```css
html {
  scroll-behavior: smooth;
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
/*
 * 1. For Androids.
 * 2. For some Androids.
 */ 

html {
  -webkit-tap-highlight-color: rgba(0,0,0,0); /* 1 */
  -webkit-tap-highlight-color: transparent; /* 2 */
}
```

* [Trick source](http://phonegap-tips.com/articles/essential-phonegap-css-webkit-tap-highlight-color.html)

Prevents iOS text size adjust after orientation change, without disabling user zoom.

```css
/*
 * 1. For iOS Safari 5.1+.
 * 2. For IE Mobile 10+.
 */

html {
  -webkit-text-size-adjust: 100%; /* 1 */
  -ms-text-size-adjust: 100%; /* 2 */
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

Removes the gray background on active links in IE 10, removes delay from tapping on links and removes gaps in links underline in iOS 8+ and Safari 8+.

```css
/* 
 * 1. For IE 10.
 * 2. For iOS 8+ and Safari 8+.
 */

a {
  background-color: transparent; /* 1 */
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

Prevents `code` content from spilling their container.

```css
code {
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
/*
 * 1. For Firefox 2+, Firefox for Android 33+.
 * 2. For IE 9+, Chrome 4+, Safari 3.1+, Opera 9.6+, Android 4.4+, IE Mobile.
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

Makes you want to click a `label`.

```css
label {
  cursor: pointer;
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
