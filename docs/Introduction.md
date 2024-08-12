# Introduction to HTML5

HTML5 is a collection of individual features. When assessing a particular browser’s HTML5 support, this is not an all-or-nothing classification; rather, you test if a browser supports a specific feature of the defined specification. Different browsers have different support for different features. This can make it difficult to target individual HTML5 elements without knowing how a user will view the document. As browsers continue to improve, cross-platform feature detection becomes less of a concern, but for now, you should always test the user's web browser for the HTML5 features you target and provide a backup solution if it fails—even if it’s just a politely worded message instructing your user to upgrade his browser.

### Canvas support

The good news, at least for this book, is that all the major browser vendors have implemented support for the canvas element. This means that you can be relatively confident that your user can see the animation you create, provided she has upgraded to a recent version of her browser.

In case the canvas element is not supported in a web browser, in your HTML document, you can provide backup content by including it within the canvas tags:

```
<canvas width="400" height="400">
     <p>This browser does not support the<code>canvas</code> element.</p>
</canvas>

// javascript check
if (document.createElement('canvas').getContext) {
     console.log("Success! The canvas element is supported.");
}
```