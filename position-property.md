# Position Property

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption><p>Overview of the Position Property</p></figcaption></figure>

> The `position` property specifies the type of positioning method used for an element (static, relative, absolute, fixed or sticky).

#### Extra Properties <a href="#f3ea" id="f3ea"></a>

`top`, `left`, `bottom`, `right` — move an element in a direction such as top, etc., so basically x-axis and y-axis

`z-index`— that is our z-axis, so the third dimension; it can create “layers” between HTML elements

## Static Position <a href="#static-position" id="static-position"></a>

[Static positioning](https://developer.mozilla.org/en-US/docs/Web/CSS/position) exists in the normal flow of the page and rejects any box offset property; it is a default position. However, the `top`, `bottom`, `left`, and `right` properties do not affect it. Note that an element with static positioning does not have a unique position. Instead, it is always set according to the normal flow of the page.

All HTML elements are static by default. Using this position, you cannot change the placement of elements on a page.

Let’s look at this example of a single `div` element with a static position:

**Example:**

```
<!DOCTYPE html>
<html>

<head>
  <style>
    body {
      background-color: #73AD21;
    }

    .box {
      width: 400px;
      height: 200px;
      background-color: white;
    }
  </style>
</head>

<body>
  <div class="box"></div>

</body>

</html>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=871f4db05c)

Here is the result of the above code:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dda3fb6f7c99_image11_246d95e27620e14f55e4fa18d722c9cb_800.png" alt="White rectangle in the upper left corner of a large green rectangle."><figcaption></figcaption></figure>

Now, let's try to move it around with the left property:

```
 .box {
      width: 400px;
      height: 200px;
      background-color: white;
      position: static;
      left: 70px;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=4b4f468499)

Here is the result of the above:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dda3fb6f7c99_image11_246d95e27620e14f55e4fa18d722c9cb_800.png" alt="White rectangle in the upper left corner of a larger green rectangle."><figcaption></figcaption></figure>

Notice that there is no difference in the image. Static positioning is not affected by the `top`, `bottom`, `left`, and `right` properties.

## Relative Position <a href="#css-relative-position" id="css-relative-position"></a>

[Relative position](https://developer.mozilla.org/en-US/docs/Web/CSS/position) is an element relative to its normal position on the page. However, the setting of a relatively-positioned element's `top`, `right`, `bottom`, and `left` properties affect its normal page position. However, any space left by the relative element will not allow any content to adjust to fit. This is because the gap bounds them in the document. Therefore, when the element with a relative position moves, no part of anything else is influenced on the screen. Still, it is as if the element kept its position on the screen and everything else flows around it as if it had never moved.

Note that changing the position property does nothing. It only starts doing something when you use one of the coordinating properties. Therefore, you set the movement values using `top`, `bottom`, `left`, and `right` to cancel the box close to the current position of the element you are moving. It's essential to note that the movement of the components works opposite of the order given and not the direction of the movement set. For example:

* Set the positive value for the `left` property to move an element to the right.
* Set the positive value for the `right` property to move an element to the left.
* Set the positive value for the `bottom` property to move an element up.
* Set the positive value for the `top` property to move an element down.

We’ll be centering the parent element in order to explain relative positioning. With this, it’s easier to understand the movement of what we will be doing:

```
<!DOCTYPE html>
<html>

<head>
  <style>
    .parent {
      background-color: #73AD21;
      border: solid 3px blue;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 500px;
    }

    .box1 {
      width: 200px;
      height: 100px;
      background-color: white;
    }

    .box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;
    }

    .box3 {
      width: 200px;
      height: 100px;
      background-color: red;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
  </div>


</body>

</html>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=0e5d47ac0b)

Here is the result:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dda3d76f7c9a_image12_c720d43eca90a247c1df32b730937796_800.png" alt="White, yellow, and red rectangles in the center of a larger green rectangle."><figcaption></figcaption></figure>

Now, let’s add the position property CSS relative to our code to move the box around:

```
<!DOCTYPE html>
<html>

<head>
  <style>
    .parent {
      background-color: #73AD21;
      border: solid 3px blue;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 500px;
    }

    .box1 {
      width: 200px;
      height: 100px;
      background-color: white;
      position: relative;
    }

    .box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;
      position: relative;
    }

    .box3 {
      width: 200px;
      height: 100px;
      background-color: red;
      position: relative;
    }
  </style>
</head>

<body>
  <div class="parent">
    <div class="box1"></div>
    <div class="box2"></div>
    <div class="box3"></div>
  </div>


</body>

</html>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=6e784f8759)

Here is the outcome:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd07876f7c8d_image9_215669f96df219354d9fc04ce7e44456_800.png" alt="White, yellow, and red rectangles in the middle of a larger green rectangle."><figcaption></figcaption></figure>

Observe that nothing changes. This is because the position property relative does nothing to the elements. You can effect change by adding any coordinating properties: left, right, top and bottom.

Next, let's move the element (`box1`) to the left and bottom:

```
 .box1 {
      width: 200px;
      height: 100px;
      background-color: white;
      position: relative;
      right: 250px;
      top: 90px;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=295345984b)

Let's look at the result to better understand how to set the value of the properties:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd7f836f7c96_image13_830fbba71d13e9fbe69f0b6fb248d0f7_800.png" alt="A white rectangle in the lower left corner and yellow and red rectangles in the middle of a larger green rectangle."><figcaption></figcaption></figure>

Notice that to move the element to the left, you need to set the value to the right; to move it to the bottom, you set it to the top. Also, it is as if the element kept its position on the screen.

Now, let’s move the element (`box2`) to the right and top:

```
.box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;
      position: relative;
      left: 100px;
      bottom: 70px;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=21cb459ba7)

Here is the result:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd501e6f7cb2_image3_6e2d3b4cb762604d73b6050d92a6a96f_800.png" alt="Three rectangles in the middle of a larger green rectangle. Two of the rectangles overlap."><figcaption></figcaption></figure>

Remember that the value was set to left to enable the element to move right; to move it to the top, you set it to the bottom. In addition, the movement of the element did not push down or influence the other elements on the screen.

## Absolute Position <a href="#absolute-position" id="absolute-position"></a>

[Absolute position](https://developer.mozilla.org/en-US/docs/Web/CSS/position) is an element with its position relative to its parent element. In this case, you remove the element from the normal document flow and do not create any gap for it in the page layout. Instead, the `left`, `top`, `bottom` and `right` values determine the element's final position.

Note that an absolute positioned element uses the document body and moves along with page scrolling. In addition, if it has no positioned ancestors, it can overlap.

For better understanding, we’ll work with these elements to explain how absolute positioning works:

```
<!DOCTYPE html>
<html>

<head>
  <style>
  body{
    background-color: #73AD21;
  }
    .container {
      background-color: red;
      border: solid 3px blue;
      display: flex;
      align-items: center;
      justify-content: center;
      width: 500px;
      height: 400px;
      position: relative;
    }

    .box1 {
      width: 200px;
      height: 100px;
      background-color: white;
    }
    .box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;

    }
  </style>
</head>
<body>
  <div class="container">
    <div class="box1"></div>
    <div class="box2"></div>
  </div>


</body>

</html>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=d98f48bcad)

Here is the outcome:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd0a606f7c7e_image2_944cb9e5c4effdd38c508128c838be79_800.png" alt="A red square inside a green rectangle. White and yellow rectangles in the middle of the red square."><figcaption></figcaption></figure>

Now, we’ll move the box. As mentioned earlier, that absolute position is an element with its position relative to its parent element.

Let’s move `box1` to the left 50px from the parent element and down 40px from the parent element:

```
 .box1 {
      width: 200px;
      height: 100px;
      background-color: white;
      position: absolute;
      left: 50px;
      top: 40px;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=bd784dab70)

Here is the result:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd41de6f7c7c_image5_d099265ddb211095c803d0d8b53f6dcb_800.png" alt="White and yellow rectangles in the upper left corner of a red square in a green rectangle."><figcaption></figcaption></figure>

Notice that the element was taken out of the document's normal flow, unlike the relative positioning, which leaves a space for a ghost element.

Next, let’s move the `box1` element to the left of 50px and the top margin of 0 relative to its parent element:

```
.box1 {
      width: 200px;
      height: 100px;
      background-color: white;
      position: absolute;
      left: 50px;
      top: 0;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=50ee41a237)

Here is the outcome:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dddcd16f7c7d_image14_13adc1871909c9407051417329aa4511_800.png" alt="White and yellow rectangles in a red square in a green rectangle."><figcaption></figcaption></figure>

The above image shows how `box1` is positioned relative to its parent element.

Now, let’s move the `box2` element to the right 50px from the parent element, and down 40px from the parent element:

```
.box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;
      position: absolute;
      right: 50px;
      bottom: 40px;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=3905459324)

Here is the effect of the code:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd18626f7c94_image1_606b7319294f035c5e74c600c2d0fd2c_800.png" alt="White and yellow rectangles in the lower right corner of a red square inside a green rectangle."><figcaption></figcaption></figure>

Notice that the element affects the flow on the page. Also, the coordinating properties work as rendered, unlike relative positioning, where you have to set `right` to move left.

Next, let’s move the `box2` element to the right 50px and to the bottom margin of 0 relative to its parent element:

```
.box2 {
      width: 200px;
      height: 100px;
      background-color: yellow;
      position: absolute;
      right: 50px;
      bottom: 0;
    }
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=8297449705)

Here is the result:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd409e6f7c98_image8_7672ee93047287793f7e822601999029_800.png" alt="White and yellow rectangles in a red square in a green rectangle."><figcaption></figcaption></figure>

This shows that `box2` element is positioned relative to its parent element, which has a bottom margin of 0.

## Fixed Position <a href="#fixed-position" id="fixed-position"></a>

An element with [a fixed position](https://www.w3.org/wiki/CSS\_absolute\_and\_fixed\_positioning?source=post\_page) is similar to an absolute element. This position is relative to the viewport, showing that it always remains in the same position even when you scroll through the page. When you see a fixed element on a page, it does not leave a gap. For example, the properties `top`, `right`, `left`, and `bottom` work as position elements. Note that fixed elements are not affected by scrolling; instead, they are in the same position on the screen.

We’ll use this image to explain the fixed position, white element and yellow element before we scroll down:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd54d06f7caf_image10_d8bdc65195f7b16ab0f023798d1f8bc1_800.png" alt="White and yellow squares on top of red text."><figcaption></figcaption></figure>

Now, let’s use two box elements to explain the fixed position. To do this, we’ll set the `box1` (white) element as the absolute position and the `box2` (yellow) element as the fixed position:

```
<style>
  body{
    background-color: #73AD21;
  }
    .container {
      background-color: red;
      border: solid 3px blue;
      display: flex;
      overflow: scroll;
      align-items: center;
      justify-content: center;
      width: 500px;
      height: 400px;
      position: relative;
    }

    .box1 {
      width: 100px;
      height: 100px;
      background-color: white;
      position: absolute;
      left: 50px;
    }
    .box2 {
      width: 100px;
      height: 100px;
      background-color: yellow;
      position: fixed;
  }
  </style>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=464a4f8dc0)

Here is the result:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470ddbc906f7c95_image7_c21d580cf1dec47521cb4ef2884fc30b_800.png" alt="White and yellow squares on top of red text."><figcaption></figcaption></figure>

Notice that the `box2` (yellow) element was not affected by the scrolling, rather, it remains fixed in the same position on the screen.

## Sticky Position <a href="#sticky-position" id="sticky-position"></a>

[A sticky position](https://blog.hubspot.com/website/css-position-sticky) occurs when an element is positioned based on the user's scroll position. The sticky position combines the relative and fixed positions, depending on the part of the scroll. In this way, it acts like a relatively positioned element. In addition, it maintains a relative position until a given offset position is met in the viewport, and then it "sticks" in place like a fixed position.

Let’s look at this example for a better understanding of how the sticky position works:

```
<style>
  .container {
    background-color: grey;
    border: solid 3px blue;
    width: 600px;
    height: 400px;
    overflow: scroll;
  }

.sticky {
  background-color: white;
  width: 100px;
  height: 100px;
  position: sticky;
  top:0;
}
</style>
```

[Save this code](https://user-96a93fbe-468f-4504-b52f-78e91ab5ec81-agyqaaz4hq-uc.a.run.app/?p=af3c48b4dc)

Below are the results of the element before and after we scroll.

The image before the scrolling:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd23b16f7cb0_image6_83218c1e92a976b9367436571dec9c79_800.png" alt="A white square between two paragraphs."><figcaption></figcaption></figure>

The image after scrolling:

<figure><img src="https://assets-global.website-files.com/6143afec68f555387049efb3/63bee44c2470dd2f336f7c97_image4_08ce271e0d5934e9215c5f9ed769d42b_800.png" alt="The white square is now in the upper left corner of the rectangle."><figcaption></figcaption></figure>

Notice that the white element maintained a relative position until it met the specified top scroll position of `top:0`. Then, it acts as a fixed position element and sticks to the specified spot.
