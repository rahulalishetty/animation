# Pixel Manipulation

The drawing API provides direct access to the pixels that compose the image on the canvas. You can create, read, and write the pixel data, which can be used to make some really cutting-edge effects and animations in the web browser.

### Getting pixel data

Direct access to the pixels is provided by the ImageData object of the canvas context. To return a copy of the pixel data for a rectangular area on the canvas element, call:

```
var imagedata = context.getImageData(x, y, width, height);
```

This returns an object containing three properties: width, height, and data. The width and height properties are the size of the image in pixels, and data is an array representing the image data.

### Accessing pixel components

The data property of an ImageData object returns a one-dimensional array containing the values of the pixel component colors in RGBA order, specified as integers in the range 0 to 255. (Note that alpha is also assigned a value in this range; not the 0.0 to 1.0 range used in the CSS-style color format.) The pixels are ordered left to right, row by row, from top to bottom.

For example, here's an array representing the image data of a 2 × 2 square. Each of the four pixels is set to full red:

```
var pixels = [255, 0, 0, 255, 255, 0, 0, 255, 255, 0, 0, 255, 255, 0, 0, 255];
```

You can access the values of any particular pixel by specifying an offset index for the array. Since each pixel is represented by four elements, you can iterate over the image data, pixel by pixel, using the following:

```
for (var offset = 0, len = pixels.length; offset < len; offset += 4) {
     var r = pixels[offset],     //red
         g = pixels[offset + 1], //green
         b = pixels[offset + 2], //blue
         a = pixels[offset + 3]; //alpha
}
```

Sometimes you may want to access the pixel at a specific coordinate in the image. Here's how you can determine its offset in the image data array:

```
var offset = (xpos + ypos * imagedata.width) * 4;
```

### Painting pixel data

To paint an ImageData object onto the canvas, call context.putImageData(imagedata, x, y), where x and y specify the top-left corner of the canvas to start drawing.

For example, to remove the red color channel from an image on the canvas, iterate over each pixel, setting its red component to 0:

```
var imagedata = context.getImageData(0, 0, canvas.width, canvas.height),
       pixels = imagedata.data
for (var offset = 0, len = pixels.length; offset < len; offset += 4) {
    pixels[offset]     = 0;                  //red
    pixels[offset + 1] = pixels[offset + 1]; //green
    pixels[offset + 2] = pixels[offset + 2]; //blue
    pixels[offset + 3] = pixels[offset + 3]; //alpha
}
context.putImageData(imagedata, 0, 0);
```