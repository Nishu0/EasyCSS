# Box Model

{% hint style="info" %}
"All HTML elements can be considered as boxes. In CSS, the term "box model" is used when talking about design and layout. The CSS box model is essentially a box that wraps around every HTML element." - [W3Schools](https://www.w3schools.com/css/css\_boxmodel.asp)
{% endhint %}

The CSS Box Model, consists of five core parts which we’ll cover:

* Border
* Padding
* Margin
* Width
* Height

<figure><img src=".gitbook/assets/box_model.png" alt=""><figcaption><p>Box Model</p></figcaption></figure>

The Box model defines the different parts of the rectangle above, which are broken up into four(4) pieces, sub-boxes or layers.

1. The innermost rectangle is the **content box**. The width and height of this depend on the element’s content (text, images, videos, and any child elements ).
2. Then we have the **padding box** (defined by the padding property). If there is no padding width defined, the padding edge is equal to the content edge.
3. Next, the **border box** (defined by the border property). If there is no border width defined, the border edge is equal to the padding edge.
4. The outermost rectangle is the **margin box**. If there is no margin width defined, the margin edge is equal to the border edge.

**Every block-level HTML element you put on a webpage is a box**. Even if it doesn't ordinarily look like it. For example, if you add a `<p>` element to your webpage and load it, it initially looks like it's just loose text. If you add some CSS colors, though, you can see the rectangle box shape**:**

```html
```

### Content and sizing <a href="#content_and_sizing" id="content_and_sizing"></a>

Let's first understand Extrinsic sizing vs intrinsic sizing

**Intrinsic Sizing**: This is like a container that adjusts its size to fit its content naturally. Imagine a box that grows or shrinks to perfectly hold whatever you put inside. It's like a rubber band that stretches or contracts to match what you put in it.

**Extrinsic Sizing**: Here, you decide the size of the container. It's like saying, "I want a box this big, no matter what's inside." You set a fixed size, and the content inside has to adapt to fit that size.

{% embed url="https://codepen.io/web-dot-dev/pen/abpoMBL" %}
Example of Intrinsic Sizing and Extrinsic Sizing
{% endembed %}

The demo showcases the text "CSS is awesome" inside a fixed-size box with a bold border. This box is set with a specific width, controlling its child content. However, there's a problem: the word "awesome" is too big for the box and spills beyond its borders. To fix this, we can make the box adapt to the text's size by unsetting the width or using "min-content," which makes the box just as wide as the smallest size needed to contain "CSS is awesome," ensuring a perfect fit.

{% hint style="info" %}
Key term: When content is too big for the box it is in, we call this overflow. You can manage how an element handles overflow content, using the `overflow` property.
{% endhint %}

