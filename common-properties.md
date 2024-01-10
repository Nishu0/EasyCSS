# Common Properties

Many of the properties available in the Grid Layout specification are universal to CSS alignment and are also used in other CSS contexts (e.g. flexbox). These properties are part of the [Box Alignment module](https://www.w3.org/TR/css-align-3/).

* `row-gap` and `column-gap` are applied to the grid container to define gutters between grid rows and columns
* `justify-items` is applied to the grid container to define justification of grid items along the row axis, within the individual grid cells
* `justify-self` is applied to any grid item to define row-axis justification within its individual grid cell
* `align-items` is applied to the grid container to define justification of grid items along the column axis, within the individual grid cells
* `align-self` is applied to any grid item to define column-axis justification within its individual grid cell
* `justify-content` is applied to the grid container to determine how to distribute unused space inside the container along the row axis
* `align-content` is applied to the grid container to determine how to distribute unused space inside the container along the column axis
* `order` is applied to individual grid items to change the order that the items appear by default in the source

Some of these general alignment features are more useful in a flexbox context, so it shouldn’t surprise you if you don’t use them much in Grid Layout.

### Grid shorthand properties <a href="#grid-shorthand-properties" id="grid-shorthand-properties"></a>

Grid Layout specification includes several shorthand properties that let you define your grids with a shorter syntax. I’ll list all of these here along with the longhand properties that they define.

Note that some of these shorthand properties accept keywords along with the represented longhand properties. Some also use a forward slash (/) in between values.

* `grid-template` – \[grid‑template‑columns] \[grid‑template‑rows] \[grid‑template‑areas]
* The `grid` shorthand is written in one of the following ways (note the keywords allowed):
  * \[grid‑template]
  * \[grid‑template‑rows] / `auto‑flow` \[grid‑auto‑columns]
  * \[grid‑template‑rows] / `auto‑flow dense` \[grid‑auto‑columns]
  * `auto‑flow` / \[grid‑auto‑rows] / \[grid‑template‑columns]
* `grid-row` – \[grid‑row‑start] / \[grid‑row‑end]
* `grid-column` – \[grid‑column‑start] / \[grid‑column‑end]
* `grid-area` – \[grid‑row‑start] / \[grid‑column‑start] / \[grid‑row‑end] / \[grid‑column‑end]
* `gap` – \[row‑gap] \[column‑gap]

\


