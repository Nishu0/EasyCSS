# Background Properties

The background properties in CSS are used to define the appearance of the background of an element. There are **eight background properties** in CSS.&#x20;

Here is a brief overview of each property:

1. **`background-color`**: This property specifies the background color of an element. The value can be a color name, a hexadecimal code, an RGB or RGBA value, or a HSL or HSLA value. For example, `background-color: green;` sets the background color to green.
2. **`background-image`**: This property specifies one or more background images for an element. The value can be a URL to an image file, a gradient, or the keyword `none` to remove any background image. Multiple images can be separated by commas. For example, `background-image: url("test.jpg"), linear-gradient(to right, blue, red);` sets two background images, one with an image file and one with a gradient.
3.  **`background-position`**: This property specifies the position of the background images relative to the element. The value can be a pair of keywords (such as `top`, `center`, `bottom`, `left`, or `right`), a pair of lengths or percentages, or a combination of both. For example, `background-position: center bottom;` positions the background images at the center of the bottom edge of the element.



    <figure><img src=".gitbook/assets/Position.gif" alt="" width="527"><figcaption></figcaption></figure>
4.  **`background-size`**: This property specifies the size of the background images. The value can be a pair of lengths or percentages, the keywords `auto`, `cover`, or `contain`, or a combination of both.&#x20;



    `background-size` can be set using a **one-value** or **two-value** syntax.

    * When only one value is provided, it sets the image’s width. Height is set automatically to preserve proportions.
    * When two values are provided, the first one sets the width, and the second sets the height.

    For example, `background-size: 50% 100%;` scales the background images to 50% of the element’s width and 100% of the element’s height. Most of the time it's used with one of two keywords

    1. `cover` - It fills (covers) the entire area of the element with the image, without stretching. Even if it means that parts of the image won't be visible.
    2. `contain` - The opposite of `cover`. It makes sure that the entire image fits (is contained) in the element, without squashing.&#x20;

    <figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>
5.  **`background-repeat`**: This property specifies how the background images are repeated or tiled. The value can be one or two keywords (`repeat`, `repeat-x`, `repeat-y`, `no-repeat`, `round`, or `space`). For example, `background-repeat: repeat-x;` repeats the background images horizontally but not vertically.

    <figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
6.  **`background-origin`**: This property specifies the origin or the starting point of the background images. The value can be one of the keywords `border-box`, `padding-box`, or `content-box`.&#x20;

    * border-box: The background image starts from the upper left corner of the border. This means that the background image will cover the entire element, including the border, padding, and content areas.
    * padding-box: The background image starts from the upper left corner of the padding. This means that the background image will cover the padding and content areas, but not the border area.
    * content-box: The background image starts from the upper left corner of the content. This means that the background image will cover only the content area and not the padding or border areas.



    <figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>


7.  **`background-clip`**: This property specifies the area or the clipping region of the background images. The value can be one of the keywords `border-box`, `padding-box`, `content-box`, or `text`.&#x20;

    * border-box: The background extends to the outer edge of the border, but is drawn behind the border. This means that the background will cover the entire element, including the border, padding, and content areas.
    * padding-box: The background extends to the inner edge of the border, but is not drawn under the border. This means that the background will cover the padding and content areas, but not the border area.
    * content-box: The background extends to the edge of the content box, but is not drawn under the padding or border. This means that the background will cover only the content area, and not the padding or border areas.
    * text: The background is clipped to the shape of the foreground text, and is only visible where the text is transparent. This means that the background will create a text effect, such as a gradient or an image.



    <figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
8.  **`background-attachment`**: This property specifies whether the background images are fixed or scroll with the rest of the page. The value can be one of the keywords `scroll`, `fixed`, or `local`. For example, `background-attachment: fixed;` fixes the background images to the viewport.







