---
layout: default
title: js
parent: Cheatsheet
nav_order: 2
---

# js

## [Swap key with value in object](https://stackoverflow.com/questions/23013573/swap-key-with-value-in-object)

```js
const swapped = Object.fromEntries(Object.entries({a: 1, b: 2}).map(([k, v]) => [v, k]))
```

## [How to make JavaScript execute after page load](https://stackoverflow.com/questions/807878/how-to-make-javascript-execute-after-page-load)

```js
window.onload = function (){};
```

## [Detect changes in the DOM](https://stackoverflow.com/questions/3219758/detect-changes-in-the-dom)

```js
var observeDOM = (function () {
  var MutationObserver =
    window.MutationObserver || window.WebKitMutationObserver;

  return function (obj, callback) {
    if (!obj || obj.nodeType !== 1) return;

    if (MutationObserver) {
      // define a new observer
      var mutationObserver = new MutationObserver(callback);

      // have the observer observe for changes in children
      mutationObserver.observe(obj, { childList: true, subtree: true });
      return mutationObserver;
    }

    // browser support fallback
    else if (window.addEventListener) {
      obj.addEventListener("DOMNodeInserted", callback, false);
      obj.addEventListener("DOMNodeRemoved", callback, false);
    }
  };
})();
```

# [How do I detect when input value changes real-time in JavaScript?](https://stackoverflow.com/questions/60353913/how-do-i-detect-when-input-value-changes-real-time-in-javascript)

```js
inputElem.addEventListener('input', () => {
  console.log(inputElem.value); // Log the new value after an input is made
});
```

# [Fastest way to convert JavaScript NodeList to Array?](https://stackoverflow.com/questions/3199588/fastest-way-to-convert-javascript-nodelist-to-array)

```js
document.querySelectorAll('img').forEach(highlight);
```

# [Creating a new DOM element from an HTML string using built-in DOM methods or Prototype](https://stackoverflow.com/questions/494143/creating-a-new-dom-element-from-an-html-string-using-built-in-dom-methods-or-pro)


```js
function createElementFromHTML(htmlString) {
  var div = document.createElement('div');
  div.innerHTML = htmlString.trim();

  // Change this to div.childNodes to support multiple top-level nodes.
  return div.firstChild;
}
```

# [How to replace DOM element in place using Javascript](https://stackoverflow.com/questions/843680/how-to-replace-dom-element-in-place-using-javascript)

```js
target.replaceWith(element);
```

# [How implement debounce for event listener](https://stackoverflow.com/questions/65035360/how-implement-debounce-for-event-listener-problem-with-storage-event)

```js
function debounce(func, wait, immediate) {
    var timeout;
    return function() {
        var context = this, args = arguments;
        var later = function() {
            timeout = null;
            if (!immediate) func.apply(context, args);
        };
        var callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        if (callNow) func.apply(context, args);
    };
};
```

# [Add a "hook" to all AJAX requests on a page](https://stackoverflow.com/questions/5202296/add-a-hook-to-all-ajax-requests-on-a-page)

```js
(function() {
    var origOpen = XMLHttpRequest.prototype.open;
    XMLHttpRequest.prototype.open = function() {
        console.log('request started!');
        this.addEventListener('load', function() {
            console.log('request completed!');
            console.log(this.readyState); //will always be 4 (ajax is completed successfully)
            console.log(this.responseText); //whatever the response was
        });
        origOpen.apply(this, arguments);
    };
})();
```