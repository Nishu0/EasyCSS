---
description: CSS Grid Explained
---

# Grid

**Let's Learn a few** CSS Grid concepts you should familiarize yourself with before diving into its usage.

**Grid container:** The HTML element on which the grid layout is applied.

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_6323267e8ec66-1024x518.png" alt="" height="518" width="1024"><figcaption><p>A grid container is what holds the grid itself. If the grid constructs a box, then the container makes up the corners of the box.</p></figcaption></figure>

**Grid item(s)**: All direct child elements of the grid container.

**Grid line:** These are the horizontal and vertical dividing lines that make up the structure of the grid. These lines reside on either side of a column (column grid lines) or row (row grid lines). Hence, a grid with four columns will have five column lines, with one after the last column.

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63232721e79d2-1024x638.png" alt="" height="479" width="768"><figcaption><p>Grid lines are the horizontal and vertical dividers (lines) that separate grid items into a grid</p></figcaption></figure>

**Grid cell**: The space between two column grid lines and two adjacent row grid lines, also known as grid tracks. It is a single unit of a grid and the smallest unit possible. By default, all grid items are laid out one item per grid cell.

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_6323275f80322-1024x638.png" alt="" height="479" width="768"><figcaption><p>A grid cell is the space between adjacent grid lines. Think of them as smaller boxes that construct the larger grid system.</p></figcaption></figure>

**Grid track**: The area between two adjacent grid lines. The gap between two grid row lines is a row track, and the gap between two grid column lines is a column track. The size of a grid track determines the width and height of our grid items.

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_632335f4c5c41-1024x638.png" alt="" height="479" width="768"><figcaption><p>A grid track is the area between two adjacent grid lines. Horizontal grid tracks are known as rows, and vertical grid tracks are known as columns.</p></figcaption></figure>

**Grid area**: A rectangular area on the grid made up of one or more grid cells. Grid areas are created when a grid item spans over one-to-many grid tracks. They must be rectangular; creating a T- or L-shaped grid area is impossible.

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_632335f582f9f.png" alt="" height="479" width="729"><figcaption><p>A grid area is a rectangular area on the grid and can consist of something as small as one cell, or as big as the entire grid.</p></figcaption></figure>

### Now, without further ado, let’s dive in!

## How to make a basic grid <a href="#make-basic-grid" id="make-basic-grid"></a>

To create a CSS Grid layout, you’ll first need to define a grid container. The grid container can be any individual parent element (for example, a div).

To define a grid container, pass [the `display` property](https://developer.mozilla.org/en-US/docs/Web/CSS/display) with either a value of `grid` or `inline-grid` to an element’s style block. Doing this will implicitly convert all direct child elements of the grid container into grid items.

```css
.block-level-grid-container {
display: grid;
}

.inline-level-grid-container {
display: inline-grid;
}
```

The value `grid` makes the parent grid element act a bit like an un-styled `div`, making it span the full width of a page by default due to them being block-level elements. In contrast, the value `inline-grid` behaves much like an un-styled `span`, making it act like an inline element to its siblings.

Let’s look at an example.

```xml
<div class="container">
        <div class="box a">1</div>
        <div class="box b">2</div>
        <div class="box c">3</div>
        <div class="box d">4</div>
</div>
Code language: HTML, XML (xml)
```

In the code block above, we define a `div` with a class of `"container"`. Within the `div` are four child elements.

We can now set the `div` as a grid container.

```css
.container {
     display: grid;
}
```

The result:

<figure><img src="https://lh3.googleusercontent.com/VXoawWo3t8LEZsDACVXI_HmKLE5x1UKiQdtChppsVNQYgtJRU6hbVJdFGB9VhfSMMqAhJmBTVUunXFuAgmNBNnXIGU_mTfvfo4Xm2hSHSTQL3-bsYFriRTYOP9VqdoC_f78jaOLBSr1lnhMtb5Xc-3Zfq-PIsTtlLvTzg47qsN-c284P6NuOW44F1g" alt=""><figcaption><p>The four elements are stacked on top of one-another vertically.</p></figcaption></figure>

Setting an element to a grid container alone will not immediately affect how the child elements are displayed, as we still haven’t specified how the layout should look. Hence, CSS lays out the grid items in a single-column grid.

To change the layout of the grid items within a grid, we must explicitly define the rows and columns we want our grid to have. To do that, we’ll use the CSS properties `grid-template-columns` and `grid-template-rows`.

#### Grid Template Columns

The `grid-template-columns` property lets us specify the number of columns we want in a grid container and how wide each column should be.

The `grid-template-columns` property accepts one or more non-negative [CSS length unit](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Values\_and\_units#lengths) values. The number of CSS-length values passed to the property specifies how many columns our grid container will have, and each value represents how wide each column (i.e., each grid track) would be.

For example:

```css
.container {
  display: grid;
  grid-template-columns: 400px 400px 400px;
}
```

The result:

<figure><img src="https://lh5.googleusercontent.com/dClQ_R4I5McKW85BH8VES6zr2tB8joHTqPaIvmToNjW555FlvCAuQ5LL21AcIkfs4uf6ZAIOlP-GEcypDETpg_j0_XYVewjqOfQK0l0KZH6llcqzhn8K5McIqYBUNZd5tRCTLTTuHRIocrmrTMCLlLvwGidF3zx541DAPWvev8VMQw7lpP_SKUZYNg" alt=""><figcaption><p>Because there are three columns, with four items, there will be two rows. The top row will have 1, 2, and 3 split into thirds, each 400px wide. The bottom row will have a 400px wide 4 element.</p></figcaption></figure>

In the example above, we use the grid-template-columns property to change the layout of our grid container to be divided into three columns, each `400px` wide.

Notice that the last grid item starts on a new row below the first three columns. That is because we only specified three columns that are each `400px` wide. Consequently, when the number of grid items in the grid container exceeds three, CSS will wrap other grid items into new rows to maintain the container’s layout.

> ⚠️ You can’t assign negative values to the CSS properties associated with the grid layout. Passing a value such as `-400px` to the grid-template-columns property will not affect the structure of a grid.

#### Grid Template Rows

The `grid-template-rows property` lets us specify the height of each row in a grid container.

Unlike the `grid-template-columns` property, it doesn’t specify the number of rows our grid container should have. It only sets the height of each row. Such behavior occurs because a grid container will implicitly create a new row whenever grid items wrap into new lines. Hence, we can’t control the number of rows that should be present in a grid using the `grid-template-rows` property.

The `grid-template-rows` property accepts one or more non-negative [CSS length](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Values\_and\_units#lengths) values where each value represents the height of each row in a grid container, from the first to the last.

For example:

```css
.container {
  display: grid;
  grid-template-columns: 400px 400px 400px;
  grid-template-rows: 100px 200px;
}
```

In the code above, values of `100px` and `200px` are passed to the grid-template-rows property. This gives the first row in the grid container a height of `100px` and the second row a height of `200px`.

The result:

<figure><img src="https://lh6.googleusercontent.com/EPr3CGbwI7jLx0GTsSCcq4T0vbUw9DK79I494Cg8S3mOiCGwpv-Ntrjarj9oiLVhn5LFbd1hNDbQRj2MY3_rWrqIJ8Iy_JXhoI4w5HW-ZpeijY9lN7s3sKa4bjtmAO07kat4eeMqAG2e3m7q1MFgIEZ6DNkzmI5YoXgt-JxkPZGTuOeZ1E1EGIs-sw" alt=""><figcaption><p>Four elements with numbers inside of them are divided into a grid. There are two rows in this grid; the first is 100px tall, while the second is 200px high.</p></figcaption></figure>

In the code above, the `grid-template-rows` property sets only the heights of the first two rows in the grid container. If we are to add more grid items to the grid container and it creates new rows to wrap them onto, the heights of these implicitly created rows will not be determined by the `grid-template-rows` property but by the size of their content.

<figure><img src="https://lh5.googleusercontent.com/LaiRX48vHFbZY2SZp-tMBHWvrH4VP7A4sEqnW6GQp0Fy6cho8HTbcRuXFGIcmxM-1D0lsGd8uWSoDfX9lPzTW2HO7_uGzm9Qd_R2jbkajzpvQBTrsapoHa9D4TV3GOCPqwLFbqRQ3uZqnXU5ByRbtbXjRjFw-BkCXHcNaq_6xSgWjiCTEmzIGe_DAg" alt=""><figcaption><p>A grid that contains twelve items and is split into three columns will create four rows. The first row is 100px high, the second is 200px, and the third and fourth are only as tall as the element’s contents.</p></figcaption></figure>

### Adding a gap between rows and columns <a href="#insert-gutters" id="insert-gutters"></a>

Adding more rows and columns to a grid container without properly spacing them apart would make the grid look too jam-packed and not helpful as a layout system. We can add gutters (spacing) between columns and rows to space them apart by adjusting the size of our grid lines. Let’s explore how we can do that.

#### column-gap

The `column-gap` property adds some spacing between columns by adjusting the width of the vertical grid lines in a grid container. It accepts a non-negative CSS length value which defines how broad the grid line between each column will be.

For example:

```css
.container { 
   display: grid; 
   column-gap: 28px;
}
```

The code above sets the width of every vertical (column) grid line in the grid container to `28px`. This adds a space of `28px` between every column in the grid.

The result:

<figure><img src="https://lh3.googleusercontent.com/LOfsGHOGi7eF9JLSZbIqUgGLtjIpa1OTy2MiZaJCxRHxWfi3l4wn0F7rqgi3AYyRh5uHNi5x6HMqMTaIq12yIjz5_7ZcvOZBRMvBntqOr7qvukOlBIptuSuZ9BF57eoAJRnWRFWrgu1-Pv0_NLvAU7TrWlWOz3jgWdlH4euub5Oemw5rJree_ykJXg" alt=""><figcaption><p>With three columns inside of a grid, there is now a 28 pixels gap to separate each column within the grid. The rows do not have a gap, as one has not yet been specified.</p></figcaption></figure>

#### row-gap

Just like `column-gap`, the `row-gap` property adds some spacing between rows in a grid container by adjusting the height of all horizontal grid lines in a grid container. It accepts a non-negative CSS length value which defines how large the grid line between each row will be.

For example:

```css
.container { 
   display: grid; 
   column-row: 40px;
}
```

The code above sets the height of every horizontal (row) grid line in the grid container to `40px`. This adds a distance of `40px` between every row in the grid.

The result:

<figure><img src="https://lh4.googleusercontent.com/5cKP16pY1nAK3BigMnhij17RZhpAGQV2byDmOtSExqjByDggZwkN99nANJeQf4ewvBo4zAi1SYWiK-AOQafEP9tmBfZrj96BM-XaSvsJ-4ukLCZ3aggAj3AAggxE9QLGqOlGnhZoTu34pObYvqaHrSd7b9HoxBVvHUqF-q23rEiKgSRJQO08gVGIEQ" alt=""><figcaption><p>There are two rows in this column, with a 40px gap between them.</p></figcaption></figure>

We can combine the `column-gap` and `row-gap` properties to space our columns and rows.

```css
.container { 
   display: grid; 
   column-row: 40px;
   row-gap: 20px;
}
```

The result:

<figure><img src="https://lh6.googleusercontent.com/0NHlyzdfg7OT__fWnpSh206SFErgOEFsHZhkB6mHB8re8_SWBFN0Xj5pePK70B61dc82433x71uszMfkyrTKCkeSvy6SHmU0pJTvE9BVcGIC5XTCRCHz3Rje31xP73SgvjGPSuccclZufZtLTWw3DR6HDfoBV6ggIeHWgtpUH6Lqv_3N_VCV-JU3Gg" alt=""><figcaption><p>A grid with rows and columns and a 20px of spacing between cells specified with the aforementioned CSS</p></figcaption></figure>

Using just a few lines of CSS, we have created a grid layout with all the basic CSS Grid properties such as columns, rows, and gutters.

### How to align content horizontally <a href="#align-horizontal" id="align-horizontal"></a>

CSS Grid exposes six properties that let us control the alignment of grid items along the [rows (inline axis) or columns (block axis)](https://developer.mozilla.org/en-US/docs/Glossary/Grid\_Axis) of a grid container. In this section, we’ll go over each property that aligns grid items horizontally along the columns of the grid container.

#### justify-items

The `justify-items` property controls the alignment of all grid items along a grid container’s inline (column) axis. It is passed to the grid container, and its value applies to all grid items within the grid. It accepts four possible values.

* **start** — aligns grid items to the beginning of all columns, which is the left edge of their cell.

For example:

```css
.container {
   justify-items: start;
}
```

<figure><img src="https://lh6.googleusercontent.com/2IPDx_J66dWMwYDzRGZigfpGjKJgRDFEoEhO5N6reUN_fFafqYt1bNZqfeWOzDaJe9yQNLHV67mlLFfu-FeW623m88Kd4jmpGmIgpvWbuCMjpFzX9XbWaVfQF3zukP2W1_nTPT1jFkgGAAVwoiXNG1mrMT3fuq7IbmJhDdWXZqc_CiYvDU4fG66yWA" alt=""><figcaption><p>Items in the container are aligned to the left of the cell</p></figcaption></figure>

* **end** — aligns grid items to the end of all columns, which is the right edge of their cell.

For example:

```css
.container {
   justify-items: end;
}
```

<figure><img src="https://lh6.googleusercontent.com/bFVQwiKLRZ7y9JeeSLxvnwCW_qDCsdsgcD8w3jedJCYvZvOO1RBN2390fPeKLJdihEH4Bl7FPV5JR-yOUVluHpwTv-L5rnOcnM5JlZWC2E5DJd4ITWZn5GAub1FwDD5APvlAp3a6sHmxmSNG8mKTFvBiTa85s6ny7UzVWHeMXeECPe9fN-5lgPgQ-w" alt=""><figcaption><p>Items in the container are aligned to the right of the cell.</p></figcaption></figure>

* **center** — places all grid items at the center of their cells.

For example:

```css
.container {
   justify-items: center;
}
```

<figure><img src="https://lh3.googleusercontent.com/pJOpNF8KRGvAAiukEFBDjaK5McxWFzOJzW7r0hASNPzJRhtu07dCC1tCcTdhYusveyno-1M7LDNv2e_BcBzkP72RVKuLfc7oFY5cncL_aWTwqKrCQJsLRXZrRfjlJ6zrwJUZt9zki8GkAZMAIOyHmuVyaKtAZEJ_GewP1Hq1lz6Te8U3mi1dryOcwQ" alt=""><figcaption><p>Items in the container are aligned to the center of the cell, with space on both sides.</p></figcaption></figure>

* **stretch** — will stretch out the grid items to fill the whole width of their cells: this is the default value of the justify-items property.

For example:

```css
.container {
   justify-items: stretch;
}
```

<figure><img src="https://lh3.googleusercontent.com/yScUKOdzpulUp5ciVkIQIssysZElUdXH0k6uHFCpt4RTmIP68A6vfyeBSRtnGIVstY3Aqo_lmuyFZRCj59B7dMi3fMg5BvUJj2OFBLzeqTe2q9JNrOoRQhL_kKDCjkXnn3YrlGg8bk2gm5SkhtJZTZKSG8dYOTePcHxbmWjq_QKgvC8LaADosPWJeg" alt=""><figcaption><p>Items in the container take up the entire space of the cell.</p></figcaption></figure>

#### justify-content

The `justify-content` property lets you set the horizontal alignment of the entire grid within the inline (row) axis of the grid container. It accepts seven possible values.

* **start** — aligns the entire grid to the left edge of the grid container.

For example:

```css
.container {
   justify-content: start;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233cee4798f-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **end** — aligns the entire grid to the right edge of the grid container.

For example:

```css
.container {
   justify-content: end;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233c40cdb9c-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **center** — places the entire grid horizontally at the center of the grid container.

For example:

```css
.container {
   justify-content: center;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233d345f5fe-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **stretch** — resizes the grid items to allow the grid to fill the entire width of the grid container: this is the default value of the justify-content property.

For example:

```css
.container {
   justify-content: stretch;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233d38d8311-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **space-around** — adds an even amount of space between each grid item, with half-sized spaces on both ends of the grid.

For example:

```css
.container {
   justify-content: space-around;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233d4700c2b-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **space-between** — creates an even amount of space between each grid item, with no space at the ends of the grid.

For example:

```css
.container {
   justify-content: space-between;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233d422eb13-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

* **space-evenly** — puts an even amount of space between each grid item and on both ends of the grid.

For example:

```css
.container {
   justify-content: space-evenly;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/img_63233d4700c2b-1024x522.png" alt="" height="522" width="1024"><figcaption></figcaption></figure>

#### justify-self

This behavior of the `justify-items` property that controls the alignment of grid items along the inline (row) axis of a grid container can also be set on individual grid items via the `justify-self` property. This property is passed to the grid items. It accepts four possible values.

* **start** — aligns a grid item to the beginning of a column, which is the left edge of its cell.

For example:

```css
.box-1 {
   justify-self: start;
}
```

<figure><img src="https://lh3.googleusercontent.com/mMg6DvdFb1vvqpJduTIDZglYnuLcB-MvA1XMeSFcN4vSfDovGtNdGQF98_CjB9ySEGI8xex-2SfS76pYbe05lISTmTJb6zZpFdNKFHdfLdHwf8gA8iDrsPOsnc1bEdWLlpLnB4RBbnX-NRumWW17jHZrDSTSmB2v4k7DtQxaYPQIPHrS8S_HIt8Wzg" alt=""><figcaption><p>The first item in the grid is aligned to the left of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **end** — aligns the grid item to the end of a column, which is the right edge of its cell.

For example:

```css
.box-2 {
   justify-self: end;
}
```

<figure><img src="https://lh3.googleusercontent.com/x3yDLrLa_f9UDD5O3Iu9VZDi31yceLNOSmqxDE9xhbZi9eejydms5V02_o7aYR8zPCkKgHt_S9DK_0KsucmVMCYsXLiQYjbfivEsxC7jKEL6Gyerhzf4xckpfpLZb7WgEgpSovvryyyCVEdcyGcikNUjhDTNAW8kdlgQ3wW9PaPYaIH40TuwT_lKjA" alt=""><figcaption><p>The second item in the grid is aligned to the right of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **center** — places the grid item at the center of its cell.

For example:

```css
.box-3 {
   justify-self: center;
}
```

<figure><img src="https://lh6.googleusercontent.com/NyJDcY0rSAa9x57POMqnjgySj-vZ4ShCfpxoXHpZwwHzlGCUrmsFNQ8O2_01l_aTLa--NVp8iVTDyddrSqEJlZBlER1aPZKeVf1RXspzqQE0hIzrfhvazXnlTQDsfy2J00_L_hIYXS8Tl48bv6o9HDvkdYVx5IYMRy81H8uBcAj6Iru2lQV4jRwoig" alt=""><figcaption><p>The third item in the grid is aligned to the center of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **stretch** — will stretch out the grid item to fill the entire cell width; this is the default value of the `justify-self` property.

For example:

```css
.box-4 {
   justify-self: stretch;
}
```

<figure><img src="https://lh3.googleusercontent.com/AkfRRzNlycOjbASCx0oqFSn_CznFPfcId0NBJQvAx1WNGkD1MzyRQFIg9O4Jzk5xVZdGlDH3W57A5h_w_pe8jQXjus-lzUv3SWqlwBnp6gWy0lj2A5bsWvziKV5ZmXsFMbCDymoOl7QrM5U8pLZbdImpVzVl2aZZamDt4thX_-Dgy4Z8Ccy1oXVWwA" alt=""><figcaption><p>The fourth grid item, like all grid items in the grid, is stretched to take up the full horizontal space of the grid cell</p></figcaption></figure>

### How to align content vertically <a href="#align-vertical" id="align-vertical"></a>

Now let’s look at the properties that align grid items vertically along the rows of the grid container.

#### align-items

The `align-items` property controls the alignment of all grid items along a grid container’s block (column) axis. It is passed to the grid container, and its value applies to all grid items within the grid. It accepts four possible values.

* **start** — places all grid items at the top of all rows.

For example:

```css
.container {
   align-items: start;
}
```

<figure><img src="https://lh6.googleusercontent.com/njewz8wPOW1NVSx52kZPiptKspeT1vS3W22PUTIfFagQUifabMzHeG6QBRKJ_LfmIH1DiZvrk6QrI2-SIbZQcKJUPiYMLmYIpNBTzpTFYkhk4_ZGzIA-FdNTqslUTna3Ov6ffUtMDLKE0QiKOX0teaE0uRbCOcARZOCpQTLrWgqAiYItoEL7v3W9kQ" alt=""><figcaption><p>The items in the grid are aligned to the top of the cell space.</p></figcaption></figure>

* **end** — places all grid items at the bottom of all rows.

For example:

```css
.container {
   align-items: end;
}
```

<figure><img src="https://lh3.googleusercontent.com/fzoIGqy6vW0-f5uK5UUMLVJYfskqeiTLhDPFXe-_5Q28At98UFhpU4SylHJgpTPsejJ6HFtHempFPlB1ev4eJ9uygoqB0CrQCU8hc5UEm7b8KZMpA0KrEmP10-LliUhpI5BqtSCtCK3nWRK6gICrKa3xHuSVqDirlGaC-Zimy7y84qf-j3ODj5etLg" alt=""><figcaption><p>The items in the grid are aligned to the bottom of the cell space.</p></figcaption></figure>

* **center** — places all grid items at the center of their cells.

For example:

```css
.container {
   align-items: center;
}
```

<figure><img src="https://lh3.googleusercontent.com/X4AWz1NuKt39_cTgMW1rxhPk5Vg77-er-uv41zyB-wUlbaVNH4N7HR_O-jpuDmzBiEZDaacsDBcx1OXNzqegN5wvEPdAJ-fGWuhpV8cxyNxyRvJ31wwzGJB2kfHlg0Ap9yEre_EANHyONYlbF-4pkoxrLPcVyUpef4p3BQxRNHbr-ElFs9l3HbLt1A" alt=""><figcaption><p>The items in the grid are aligned to the vertical center of the cell space.</p></figcaption></figure>

* **stretch** — will stretch out all grid items to fill the entire height of their cells; this is the default value.

For example:

```css
.container {
   align-items: stretch;
}
```

<figure><img src="https://lh6.googleusercontent.com/wBtpdmGcK4jnLzFe7eGFzJKb_16Td7CFZsmv3hQE_LZ7oYf9dNC9M0XWXTtKF1hZauTfXRfAms1pw4cLuysS5aqEW8urr2wlRWhbdQuddUovDVfSkdh5C8z7UGYJWbqX2wo--jpUIqOuLFuF2oOk0m68juRATDdint8aoB7SqOgYtH5LP3-va9KlFA" alt=""><figcaption><p>The items in the grid are stretched to take up the full vertical space of the cell space.</p></figcaption></figure>

#### align-content

The `align-content` property lets you set the vertical alignment of the entire grid within the block (column) axis of the grid container. It accepts seven possible values.

* **start** — aligns the entire grid to the top of the grid container.

For example:

```css
.container {
   align-content: start;
}
```

<figure><img src="https://lh6.googleusercontent.com/mfLzck8xvPZJCj4p9vAKjkpN6wbtSrHScRS2CobDqLjHtXc2MACiao4OM9tnodhFLwpobICREL0TQUteoamfQFy2_tKuXl3VlikVXIvNe_-ZeF8d51nP4HDyfbQ1tEoD3_MJwJ3OE1b9mMbGnWVHF710a4BMx43MCauRfn2MykObfR3Evxc5tYkuxA" alt=""><figcaption><p>Grid items spaced near the top of the grid. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

* **end** — aligns the entire grid to the bottom of the grid container.

For example:

```css
.container {
   align-content: end;
}
```

<figure><img src="https://lh3.googleusercontent.com/ZdWM6ZK86Kvzj-1T5CAqCXiBc2eHWoRfYf6-swRS2Tgya5AzJlTnju2KxTxKHw2QEkgr0VrIXQJRIKMLCc6wxPYbPQc3kVxNEoKRKbwyNSlxn6z1yKgRPIFxwfKladrgyBDCN7X03KzhNcolTGmz6i2gm07EDzW7sY8h2wNMw9vnP2eN5-lCnBZtLA" alt=""><figcaption><p>Grid items spaced near the bottom of the grid. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

* **center** — places the entire grid vertically at the center of the grid container.

For example:

```css
.container {
   align-content: center;
}
```

<figure><img src="https://lh5.googleusercontent.com/q5xJoTSWvwa2g6Af_cj9EOJ4_7xkurZn392oIgKHLLKg5MiLbihj6rgYgHjrKhqBLmq6WNRxpcO9qQ-RdKeSY-FqTehi6dcH-9EHLr_a675M401xm2Bmp7xtHNDc6avoK8_zvQXr9LelTHsDUe05PLzhqT56omQ6XqTz0Vg-CASoxv2TKtkow0UNwA" alt=""><figcaption><p>Grid items spaced in the center of the grid. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

* **stretch** — The grid items stretch to fill the full height of the container grid; this is the default value.

For example:

```css
.container {
   align-content: stretch;
}
```

<figure><img src="https://lh3.googleusercontent.com/QMWt_Z9x5BsHmhEHHeWXtjTuTAyccdE36nrHkLWWELf6SK7WVW4ZYum81dkK4q8lR4JKaHBXONvYXLV7Cfb6xS16OxeD24VgeUI5RQFSbFwNmY2fR25MXWVnHDSLCW_StFsMO_gr5AdKCSq-ys1_NS_QhzsfPMHhB6RJ4LMJ1SAXWiM_SFYQ4IFPeA" alt=""><figcaption><p>Grid items stretched evenly across the grid. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

* **space-around** — creates an even amount of space between each grid item, with half-sized spaces on both ends of the grid.

For example:

```css
.container {
   align-content: space-around;
}
```

<figure><img src="https://lh5.googleusercontent.com/Xmx7kD6Mk9NDW9Uap7cYYLy4Ohn1Nyf3c1-KVm5bdQeYiEybXq2UeYQx8EHnGCAjlteMwSsGsc-lfg4ozJfZ0vbZFqXuDPkwTRYt3_NK7aLHXSo427E8-DwdJeS329buO8i5O1ykPk_iC3_uWN3TQqy-NC6yZwQDIeI-MZ-sAB-7Xj_cgpivKIpB6A" alt=""><figcaption><p>Grid items spaced with top and bottom spacing each half the size of the middle spacing. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a></p></figcaption></figure>

* **space-between** — adds an even amount of space between each grid item, with no space at the ends of the grid.

For example:

```css
.container {
   align-content: space-between;
}
```

<figure><img src="https://lh3.googleusercontent.com/YHDqpOlvwSpMkMCk7liGTtNEYXuQHwhh36cfQEXSxRYubd2pE4Jf3tysZtolnHDHgMVsN-XCDbbkFIqG27aiiEXZplLFpK2gVkbImJaZHeCZgtK9oGEn8_BUTKKKKcgJeLQPAyOrYR9wM3sjQlFtHZ7WCDXf_ltKlUC3U0kDu7NGg-ovryCWr_gbpQ" alt=""><figcaption><p>Grid items have large space in the vertical-middle. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

* **space-evenly** — places an even amount of space between each grid item and on both ends of the grid.

For example:

```css
.container {
   align-content: space-evenly;
}
```

<figure><img src="https://lh6.googleusercontent.com/rQFpvpx9PsZIBC37QaZPJZFjP2lpn-UQ2i6C2UBCsNuXAZlRsjOCgpvd1lPFH293IVbTohtraZy1ifrh5ZOrrJLiE1t1u_eEBMdJe8ormCmky3-MabQeA-uDbXqNoP_cOPtH6EFxjwTkUxL5lCiynjyrHRL6jWo-sQ1h7rKR8oPQ7qSKbjhRk-VEWw" alt=""><figcaption><p>Grid items have even spaces in the spaces between them. Image captured with help of <a href="https://www.w3schools.com/css/tryit.asp?filename=trycss_grid_align-content_center">W3 Schools</a>.</p></figcaption></figure>

#### align-self

This behavior of the `align-items` property that controls the alignment of grid items along the block (column) axis of a grid container can also be set on individual grid items via the `align-self` property. This property is passed to the grid items. It accepts four possible values.

* **start** — places a grid item at the top of its cell.

For example:

```css
.box-4 {
   align-self: start;
}
```

<figure><img src="https://lh5.googleusercontent.com/fATY8sjc-5PGkpENqd4pqHBBwrxt5nE5wlavDtZxTjFUiJtceR6bCfBOLUQ_jk1x8-W4iuMIjpD41LZ_-G0v3SdzpIgoOVxa_Gsoz-bPRLTd_qzvxX41cflooVGyHxgaL68vgt5xrXLG_qCw7uT2S1BPwYjyV_OeHxmJw01-Kbkh6l3Ih_yqkkwa6A" alt=""><figcaption><p>The fourth item in the grid is aligned to the top of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **end** — places a grid item at the bottom of its cell.

For example:

```css
.box-5 {
   align-self: end;
}
```

<figure><img src="https://lh6.googleusercontent.com/RDkLUmgFOo9zwHWliP3mtfjhNt02LuikYby45Sbs1HjceDiSa8Y3BZDQTKicv544GNPZB3MfE57J4R9I7AXPYJLxVm9fnCHOZzrGpwsh7ULeSpbtC1sYNyBtrqu3tKg2whLjdE5-6ywPOsEpMSCXoxGnM7jwH63rpJPKfnZbuSlvj87q5UTaUnkXrQ" alt=""><figcaption><p>The fifth item in the grid is aligned to the bottom of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **center** — places a grid item at the center of its cells.

For example:

```css
.box-6 {
   align-self: center;
}
```

<figure><img src="https://lh5.googleusercontent.com/GIhfPU42FXym-wVrO-oM5qATUwOEsCeKF-hFrH55KU2k18hTxul69ipZEeGnfx6oywZ8VrW-zvo12nETKpGurt6l-m-qSLRI00my7v-nJesx8na6ZQb4PGV2-5KbcSzVtBkPK5ZqbuK_hLNzIw933_ZqFyiarBsqSUCrlNa2kDxq-26NHiFZk_KihA" alt=""><figcaption><p>The sixth item in the grid is aligned to the vertical center of the cell space, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

* **stretch** — will stretch out the grid item to fill the entire height of its cell; this is the default value.

For example:

```css
.box-1 {
  align-self: stretch;
}
```

<figure><img src="https://d2h1bfu6zrdxog.cloudfront.net/wp-content/uploads/2022/09/image-20.png" alt="" height="192" width="704"><figcaption><p>The first grid item, like all grid items in the grid, is stretched to take up the full vertical space of the grid cell.</p></figcaption></figure>

### Introducing new measurement units <a href="#grid-measurement-units" id="grid-measurement-units"></a>

Aside from non-negative [CSS length](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Values\_and\_units#numbers\_lengths\_and\_percentages) values such as `px`, `rem`, `vw`, and percentages (`%`), you can also use special sizing units and keywords to control the size of grid items in a grid.&#x20;

#### The fractional (fr) unit

The `fr` unit, short for “fractional,” is a length unit introduced with the CSS Grid layout. It represents a fraction of the free space available in a grid container. This makes it the ideal unit for defining responsive columns and rows that will scale as the browser’s viewport shrinks and grows.

Let’s look at an example to explain how helpful the `fr` unit is and why it’s a better alternative to other CSS length units.

Say we are to create a grid layout made up of three columns where the first column takes up 1/6 of the grid’s width, the second column takes up twice the width of the first column, and the third column takes up three times the width of the first column.

If we weren’t using the `fr` unit in the example above, we’d have to perform some math on our end. We had to figure out the total width of the grid (100%), divide that by 6, then multiply whatever the result is by how wide each column should span, which would be:

* width of first column = 100% / 6 \* 1 —> 15%
* width of second column = 100% / 6 \* 2 —> 30%
* width of third column = 100% / 6 \* 3 —> 45%

As the layout becomes more complex, using percentages or any [CSS math function](https://coderpad.io/blog/development/an-overview-of-five-css-math-functions/) becomes unsustainable. This is when the `fr` unit comes in handy.

The `fr` unit tidies all this by letting us specify how the available space in a grid container should be distributed among its rows and columns. Then it spreads the space available in that order.

```css
.container {
   display: grid;
   grid-template-columns: 1fr 2fr 3fr;
}
```

In the code above, we assign a fraction of the available space in a grid container to the first column, then twice to the second column, and thrice to the third column.

The result:

<figure><img src="https://lh4.googleusercontent.com/o2_OEa_aixFsTRUcbe0LFBzTgIArTBEpQwkqiZFEFcJ3Kyk8hl8Moa6HRrrGjId3PKcl8rvD9VadqauWw9MNhRxIdm_mQBz4NeHUqPrNyAX4FM-M-6QDZf4JU1tmc268_9GVzqEB1geAAbKa8-471QHWhEvR1cQjrm-BRQTwHs1AvpFglkvI87QtBg" alt=""><figcaption><p>A grid that consists of three columns and two rows. The first column is one-third the size of the last column and half the size of the second column.</p></figcaption></figure>

#### min-content

The `min-content` is a sizing keyword that sets the width of a grid track to its [intrinsic minimum width](https://developer.mozilla.org/en-US/docs/Glossary/Intrinsic\_Size), which is usually the size of the smallest content or text within its grid items. It works similarly[ to the CSS function `min`](https://coderpad.io/blog/development/an-overview-of-five-css-math-functions/#min), but is used as a spacing unit instead of a function.

When applied to a column or row, they become as narrow as the longest word in their track. This lets you get the shortest measurement of the content inside the grid items.

For example:

```css
.container {
   display: grid;
   grid-template-columns: 1fr min-content 1fr;
}
```

In the code above, we set the first and third columns to be as wide as a fraction of the grid container while passing the `min-content` to the second column, making it shrink to the size of the words in its grid items.

The result:

<figure><img src="https://lh5.googleusercontent.com/nYF4gWJqbZgV2eRfIb-8ZJMmX0giKBMUR3T33Xc8l5cqiFYIjIS6VrP5o3O3XANO_d7WstGgQA6kKHFnyYNMb8FN4pTyhRNyQ7dsZUhl8MdqG1JvpSeKzEg2NgglDBNlKBVx1DAwAws-eWnvPm6fsGM9QF8roHLQJ2U4nJD3SBo7gm9TtJCShMz-IQ" alt=""><figcaption><p>A grid with three columns. The middle column only takes up the smallest amount of space needed to display a single character, while the first and last columns take up all remaining space.</p></figcaption></figure>

#### max-content

The `max-content` sizing keyword has the opposite effect of `min-content`; `max-content` behaves similarly to [a CSS function: `max()`](https://coderpad.io/blog/development/an-overview-of-five-css-math-functions/#max). When applied to either a column or row, the track becomes as wide as possible for all the content within the grid items to display in one long unbroken line.&#x20;

The most significant benefit of using `max-content` is that you can let the content within our grid items breathe and spread out rather than wrapping them into new lines, which causes vertical text overflows.

For example:

```css
.container {
   display: grid;
   grid-template-columns: 1fr max-content 1fr;
}
```

The code above defines three columns and sets the width of the second column to the `max-content` keyword. If we add a lot of words to the grid items in the second column, the text in these grid items won’t overflow. Instead, the width of the second column will grow, and the first and third columns will shrink to accommodate it.

The result:

<figure><img src="https://lh5.googleusercontent.com/PmBAo8AsGwCj0IxKzxmVjBH1c0ABLCLENdH4MQRAqDswyKH-33UzQNuYNrcfMIa6TIfAyfVOMLcnMosgaaI62-InUl8bHQ9dmyOvWvMAwvF7jpLaPmHKRk95n6SGuSh21VPu6kJcbtM_nYAA2ki2DhvEcEHonOXuzaXrPxbfVjZj5sAm6yhwNpBUew" alt=""><figcaption><p>A grid with three columns. The middle column has a sentence that’s not broken into newlines, but rather stretches to fill as much space as it needs and no more. The first and last columns take up all remaining space.</p></figcaption></figure>

### Useful CSS functions to combine with CSS Grid <a href="#useful-css-functions" id="useful-css-functions"></a>

When working with the CSS Grid layout, there are a few handy functions you should familiarize yourself with to help increase the efficiency of your CSS.

#### repeat()

The `repeat()` function lets us define recurring unit declarations for our grid container’s rows or columns in a more compact form.

For example, suppose you repeat unit declarations when defining columns or rows using the `grid-template-rows` and `grid-template-column` properties. You can use the `repeat()` function to declare these recurring patterns more concisely.

The function takes two arguments:

* **repeat count:** this is an integer value of 1 or higher, or the keyword values [auto-fill](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat#auto-fill) or [auto-fit](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat#auto-fit). It specifies the number of times the recurring pattern of the rows or columns should repeat.
* **track(s) definition**: this is where we specify the recurring pattern of rows or columns to repeat. We can pass one or more non-negative length values to it, where each value represents the size of a row or column.

Essentially, its syntax is this:

`repeat(<number of columns/rows>, <the height or width of each column /row>);`

Say we want to create a grid with six equal columns. Without the `repeat()` function, we’d have to explicitly define each column using the grid-template-columns property.

```css
.container {
     display: grid;
     grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
}
```

However, as the number of columns increases, this approach becomes unsustainable and verbose. We can rewrite this into a more compact form using the `repeat()` function.

```css
.container {
     display: grid;
     grid-template-columns: repeat(6, 1fr);
}
```

Here we use the `repeat()` function to create a column that spans over a fraction of our grid container, repeating the process six times. This drastically reduces the number of repetitive unit declarations in our CSS.

The result:

<figure><img src="https://lh3.googleusercontent.com/eaLX5z6FTVI0VCldQBosUYDtTrPQYZe38y0O3YDVAMN29C_7Hya-M4lrZVeVp6wKNVnjuqO66fyp7-KcJU10eYh62mjE85Bsv-n5JZrmWnePdPnCAojX1-5lYq5oDSAbUUVuBnq0nQ6sfL85lcpyyct29rDSwiVeVObUM0SsjzkzgzOAdbQ9BA7k-Q" alt=""><figcaption><p>Six evenly spaced items in a row.</p></figcaption></figure>

#### minmax()

When defining a responsive grid layout, you likely want to give each grid track a minimum and maximum size to ensure that they scale up and down to fit their content as the viewport resizes. This is where the `minmax()` property comes in handy.

The `minmax()` function lets us specify a minimum and maximum size for a grid track. As the grid is resized across viewports, the grid track will grow and shrink across that range. On smaller screens, it will shrink until it reaches the minimum size. And on larger screens, it will stretch until it reaches the maximum size.

The `minmax()` function takes two parameters, `min` and `max`, where:

* min is the minimum size of the track.
* max is the maximum size of the track.

Syntax:

`minmax(<minimum allowed value>, <maximum value>);`

The `minmax()` function also accepts CSS Grid sizing units, keywords, length and percentage values.

Let’s look at an example using the `minmax()` function.

```css
.container {
  display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-template-rows: repeat(2, minmax(100px, max-content));
}
```

In the code above, we use the `minmax()` function to set the minimum height of the two rows in our grid container to 100px and the maximum height to `max-content`, which ensures each row stretches and becomes as wide as possible to contain its contents if it gets taller than `100px`.

The result:

<figure><img src="https://lh3.googleusercontent.com/Fdl77Um2hpublshpNBR4l-G19W25NIIL7uVfSJgVpLdKFZK2Hi70gblaxeEGm-6btPY_7cP4n4YKpKZ913GR2cIAOFI837QPPtDpCrT0LqwfiA8uMWmpDSFnHtGoFbARcI0YevcCOkWq_IluvlE9Wzgk-OVZs_1VEFjM7VJY3vq-9QNf3zpq27Lp4w" alt=""><figcaption><p>Two rows and three columns. The three columns have equidistant widths. The first row has 100px height, and the second has the height of a paragraph inside one of the cells.</p></figcaption></figure>

A significant benefit of the `minmax()` function is that it reduces the need for media queries. Rather than relying mainly on media queries to control the size of grid tracks (columns and rows) across viewports, it lets you set up, to a degree, a responsive transition of values for a grid track.

#### fit-content()

The `fit-content()` function operates similarly to the `minmax()` function. The difference is that with `fit-content()`, the minimum value is the size of the content within the grid item, and the maximum value would be the value we pass to it. This lets you clamp your content to the smallest value and scale it up to a certain value as needed.

When applied to a grid track, it sets the size of the grid track to its intrinsic minimum width, which is the size of the smallest piece of content or text in its grid items. The caveat is that the smallest piece of content or text size is not larger than the value specified in the function.&#x20;

However, if the value of the intrinsic minimum width exceeds the value supplied to the function, the size of the grid track is set to the value passed to the `fit-content()` function, and the content of the grid items will begin to wrap.

For example:

```css
.container {
   display: grid;
   grid-template-columns: fit-content(200px) fit-content(300px) fit-content(400px);
}
```

The code above creates three columns with widths of 200px, 300px, and 400px, respectively, using the `fit-content()` function. This means that the size of each column will be equal to the size of the smallest piece of content or text in its grid items, but if that becomes greater than the value supplied to the `fit-content()` function, then the size of the columns will be set to the value passed to the `fit-content()` function.

The result:

<figure><img src="https://lh4.googleusercontent.com/6_tL1f9PGuW_LJpOkE0BK7E1FCrhQUYZ6RQOq23zJuR2mJGrwyUSxgLNvEIUwxQzJpOc7o8lqmeZX0mNf-hKe_NEEo6dMo667TrCxGcD7IwlsEAYeiiYzBBeu7ETvgXNVfvQ8PkywlOXdABUfafHWSp5JfWaHDHQHa7b8NosxmA7Pl-Fh6PlpD9tCg" alt=""><figcaption><p>A grid with three columns. The first and third columns are only as wide as a single character, since that’s what they contain. The middle column is 300px wide because there’s a paragraph in the middle of it.</p></figcaption></figure>

### Expanding grid items across multiple grid lines <a href="#expand-grid-items" id="expand-grid-items"></a>

Remember, when talking about grid lines, the horizontal lines reside on either side of a row (known as row grid lines), and the vertical lines reside on either side of a column (known as column grid lines) within the grid container.

In the grid container, each grid line is given a number based on its position on the grid. The first grid line (row or column) is given the number 1, the second 2, and so on.&#x20;

For example, the image below displays the number of grid lines present on a grid container with three columns and two rows, where the column lines are the numbers inside the orange circle from 1 – 4, while the row lines are the ones inside the blue circle from 1 – 3.

<figure><img src="https://lh4.googleusercontent.com/z1Txqjd8Ljujmfdol2JQpbX_WYI6yiO-ij5crG7QWYOqMJb9rHpHutND_CznY_u8e8dvom8ZWAnQq2dhSoLyZBtLmKU6Y-VRIKbxph93-LUxdsDHqX6omASowG18Pf4s-UfX9NHuVdDDzELqxyXbIJSyRz1Bz1fxuChkj8s-PyNaqXnoeDDauuad8g" alt=""><figcaption><p>A grid system with the lines numbered as described previously</p></figcaption></figure>

The browser uses these grid lines to control the layout and position of items within the grid. For instance, in the image above, the first column spans from column line 1 to column line 2, and the first grid item will be placed between those lines and span that wide. However, a handful of CSS Grid properties let us control the position of grid items along these grid lines and how wide they would span horizontally and vertically across them.

The properties you can use to control the position of grid items and how they span across these lines are:

* `grid-column-start`
* `grid-column-end`
* `grid-row-start`
* `grid-row-end`

Let’s go over each in detail.

#### grid-column-start

The `grid-column-start` CSS property lets us specify the horizontal starting position of a grid item along the column grid lines within the grid container. This start position defines the start of the left edge of the grid item.

Using the grid layout below, let’s target the first grid item and set its horizontal starting position to column line 2.

<figure><img src="https://lh6.googleusercontent.com/cpqXH1DdnU-5uZRWzkZHbTR-FHwgxjHcChzyQgo1c4rGgoUNSCrMZGSLFWIiQKAgEJz0ZjldQ6FYAyVmzd989CneRZT15E3-KlhJbu6_AFBCeDw5zzfkGHJvc1RjzC6zkJM1np2f3XXB9t8UC4YYNZM0Th509l_0pwHtzH6IUSLXIMdoTOmn5YAzqQ" alt=""><figcaption><p>A grid with two rows and three columns with each cell area numbered. The first row is “1, 2, 3,” and the second row is “4, 5, 6”</p></figcaption></figure>

We can target the `div` using [CSS pseudo-selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), or you can apply classes to the element and target it with that.

```css
.container div:nth-of-type(1) {
  grid-column-start: 2;
}
```

Doing this, the horizontal starting position of the selected grid item will be on the second vertical grid line (column line 2).

<figure><img src="https://lh4.googleusercontent.com/IjnVjdIP3ND3JhKeuh01Lpbvexj5tkOfa1CLQ9xrfuk0nR8nPwYBmO6aavZLV0vgsJYo_e4-a4pCUE-mG634mmbx3KmHvB44AT5f0RofdBtrocQgUHp3r1k-u82JmXk0lebhS35Sm354ky1lwoR--pOly7Deq6cnc0KUciSBASpPV98qqt6d1bNhKw" alt=""><figcaption><p>A grid with three rows and three columns, and six items. The first item in the grid starts on the second column, which shifts every numbered cell item to the right by 1, overflowing to the left.</p></figcaption></figure>

From the image above, the first grid item now begins at column line 2, while the other grid items are pushed over, wrapping onto new rows or creating empty spaces on the grid.

#### grid-column-end

Along with specifying the horizontal starting position of a grid item with `grid-column-start`, we can set where the grid item should end using the `grid-column-end` property.

For example:

```css
.container div:nth-of-type(1) {
  grid-column-start: 2;
  grid-column-end: 4;
}
```

This makes the first grid item start on column line 2, span across two grid lines, and end on line 4. Using the `grid-column-start` and `grid-column-end` properties, we can effectively control the horizontal starting position of a grid item and how wide it spans across the grid.

The result:

<figure><img src="https://lh4.googleusercontent.com/_SsdpX_A41oJJ9qjrDSOevdB-IcBBiY5Ovb4rSfknxyhnB0IyOA8-16aI70FUj6T5OYw8xCol6MUNKzWWaOuHNAQLiIlIZUY_GTwU5wS8Yei0Y73TCaAN3fDexh6PxK1buW7R-tTjohW5RRHfxpxj7nkiUijpKkqQn8DLivgGFBo76F5i5IHv79Ksg" alt=""><figcaption><p>A grid with three rows and three columns, and six items. The first item in the grid starts on the second column and spans into the third column, which shifts every numbered cell item to the right by 2, overflowing to the left.</p></figcaption></figure>

#### grid-row-start

The `grid-row-start` property lets us specify the vertical starting position of a grid item along the horizontal (row) grid lines within the grid container. This sets the line where the grid item begins.

For example:

```css
.container div:nth-of-type(2) {
  grid-row-start: 1;
}
```

In the code above, we set the vertical starting position of the second `div` element to row line 1 using the `grid-row-start` property.

The result:

<figure><img src="https://lh3.googleusercontent.com/mGMrXg1c-IJxlt0uQJ_GHVLEsekwlnbRx7Iq4dh9BFy8evS7mv3Y2DCqjtbEKd6n_w0BFmgHafVaiX86h-oxd6TayU99PV7dWHgFQ7WgW4cAYQGZlPNvhZpXqBVEUyGNQeNTy5lAafvQlmWEzEJiCrSlMrki51Vu7CzyWkg4w3YgFYZw_io6fhJ6Jg" alt=""><figcaption><p>A grid with three rows and three columns and six items. The order of the items is: “2, 1”, “3, 4, 5”, then “6” on each row, respectively.</p></figcaption></figure>

#### grid-row-end

The CSS `grid-row-end` property lets us specify the vertical ending position of a grid item along the horizontal (row) grid lines within the grid container.

For example:

```css
.container div:nth-of-type(2) {
   grid-row-start: 1;
   grid-row-start: 4;
}
```

This makes the second grid item start on the first-row line and span down three grid lines, ending on line 4. Using the `grid-row-start` and `grid-row-end` properties, we can effectively control the vertical starting position of a grid item and its height down the grid.

The result:

<figure><img src="https://lh4.googleusercontent.com/c9H5Can2wpoOynFXmiqDSLDk8FDObICIT6lo2pC46JPouac-I8mvmLIdcoqscyjaFBd1ksfA3vhvNykq-dzOMdRzQKWKutGnJ_MINhxM1iznDTfvW0hQdQ-MbTtmkiXNcPqQsL5FW6m0sWYz6UHhccCtHr62SBtVLaH6fru00J0rIfThr-OFydVpOA" alt=""><figcaption><p>A grid with three rows and columns. The first item starts on the second column and stretches to the third column on the first row. The second item starts on the first row and stretches to the third row on the first column. The last four items make up a two-by-two square in the bottom left corner.</p></figcaption></figure>

### CSS Grid shorthands <a href="#css-shorthand" id="css-shorthand"></a>

Like most CSS properties, CSS Grid offers a handful of shorthand properties that provide a shorter and more forward way to set the values of multiple CSS Grid properties simultaneously. Using these shorthand properties, we can write more concise (and often, more readable) style sheets, saving time and energy.

Let’s take a look at these properties.

#### Using a single CSS rule to set all gutters in a grid

In this guide, we have seen how we can add gutters (spacing) between columns and rows to space them apart using the `column-gap` and `row-gap` grid properties. Using a single property — `gap`, we can set the values for both the `column-gap` and `row-gap` properties.

The `gap` property is a shorthand for the row-gap and column-gap properties. It lets us add gutters (spacing) between columns and rows.

Syntax:

`gap: <row-gap> <column-gap>`

The gap property accepts two values where:

* `<row-gap>` is the first value passed to the gap property. It sets the value of the `row-gap` property.
* `<column-gap>` is the second value passed to the gap property and sets the value of the column-gap property. It is an optional value, and if omitted, it’s set to the same value as `<row-gap>`.&#x20;

For example:

```css
.container {
   display: grid;
   gap: 20px;
}
```

This adds a space of `20px` between all columns and rows in a grid container and is the same as the code below.

```css
.container { 
	display: grid; 
	column-row: 20px;
	row-gap: 20px;
}
```

#### Combining horizontal and vertical alignments into single CSS rules

We talked about the six CSS Grid properties that let us control the alignment of grid items along the rows (incline axis) and columns (block axis) of a grid container. In this section, we’ll go over the shorthand properties that let us set the alignment of grid items much better.

**place-items**

`place-items` is a shorthand property that lets us set the values for the `align-items` and `justify-items` properties in a single declaration. It allows us to control the alignment of all grid items horizontally and vertically at once.

It accepts two values: the first value sets the value of the align-items property, and the second sets that of the justify-items property. If the second value is not specified, the first value will be assigned as the value of both properties.

For example:

```css
.container { 
	display: grid; 
	place-items: center; 
}
```

This sets the value of both the `align-items` and `justify-items` properties to `center`, placing all grid items at the center of their grid areas.

**place-content**

`place-content` is a shorthand property that lets us set the values for the grid properties `align-content` and `justify-content` in a single declaration—enabling us to control the horizontal and vertical alignment of the entire grid within the grid container at once.

It accepts two values: the first value sets the value of the `align-content` property, and the second sets that of the `justify-content` property. If the second value is not specified, the first value will be assigned as the value of both properties.

For example:

```css
.container { 
	display: grid; 
	place-content: center; 
}
```

This sets the value of both the `align-content` and `justify-content` properties to `center`, centering the entire grid within the grid container horizontally and vertically.

**place-self**

`place-items` is a shorthand property that lets us set the values for the `align-self` and `justify-self` properties in a single declaration. It enables you to control an individual grid item’s horizontal and vertical alignment within its grid area.

It accepts two values: the first value sets the value of the `align-self` property, and the second sets that of the `justify-self` property. If the second value is not specified, the first value will be assigned as the value of both properties.

For example:

```css
.item { 
   place-self: end center;
}
```

In the code above, the value of the `align-self` property is set to ‘end,’ which pushes the grid item vertically down to the bottom of its grid cell. And the `justify-self` property is set to `center`, which places the grid item horizontally at the center of its cell.

The result:

<figure><img src="https://lh5.googleusercontent.com/AMQoM98peJpRTdHac4FwXFTFDOffwU2kQrm18tQJGcM3czqqFNfz0TAtnu7L_2hKbQRORM8LtjiabfcYybNHwrGtszZqPWsCRz7qNivoh6JvB8B8kJmPcTutZEptwsRjJM8wdIbyq34znfECuONXIVuTymfLAoyKrUfMGqOOM_WPjNNPUnutjTZFBw" alt=""><figcaption><p>The first grid item in the grid is aligned to the vertical end of the cell space and horizontally at the center, while all of the other items stretch to fill the cell area.</p></figcaption></figure>

#### Shortening the CSS for spanning grid items across columns and rows

Declaring the ‘grid-column-start,’ ‘grid-column-end,’ ‘grid-row-start,’ and ‘grid-row-end’ attributes anytime you want to span a grid item across some columns and rows can be somewhat redundant. Let’s look at some shorthand properties that can help us declare the CSS to span grid items more concisely.

**grid-column**

The grid-column is a shorthand property for the `grid-column-start` and `grid-column-end` properties. It lets us specify the horizontal starting position of a grid item along the column grid lines within the grid container and where the grid item should end.

Syntax:

`grid-column: column-start / column-end;`

The grid-column property accepts two grid line values separated by a slash (/) where:

* The first value, `column-start`, is the value of the `grid-column-start` property.
* The second value after the slash, `column-end`, is the value of the `grid-column-end` property.
* And the slash (/) serves as a demarcation between these two values as both can contain one or more whitespaces. As a result, passing the slash is required to eliminate errors and ambiguity. Also, as a best practice, adding some whitespace at both sides of the slash (/) is recommended to make our CSS more readable.

For example:

```css
.gird-item {
  grid-column: 1 / 4;
}
```

The code above tells the grid item to span horizontally from column line 1 to column line 4 in the grid.

**grid-row**

The `grid-row` property works just like the `grid-column` property. It is a shorthand property for the `grid-row-start` and `grid-row-end` properties. It lets us specify the vertical starting position of a grid item along the row grid lines in the grid container and where the grid item should end, spanning down the grid.

For example:

```css
.gird-item {
  grid-column: 2 / 5;
}
```

This causes the height of the grid item to span down from row line 2 to row line 5 in the grid.
