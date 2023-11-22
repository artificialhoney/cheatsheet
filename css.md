---
layout: default
title: css
parent: Cheatsheet
nav_order: 2
---

# css

## [@media print issues with background-color](https://stackoverflow.com/questions/3893986/css-media-print-issues-with-background-color)

```css
.page {
    background-color: white !important;
}
```

## [How do I preserve line breaks when getting text from a textarea?](https://stackoverflow.com/questions/40417527/how-do-i-preserve-line-breaks-when-getting-text-from-a-textarea)

```css
textarea {
    white-space: pre-wrap;
}

```

## [Changing the text selection color using CSS](https://stackoverflow.com/questions/10578073/changing-the-text-selection-color-using-css)

```css
::selection {
    background-color: #352e7e;
    color: #fff;
}
```