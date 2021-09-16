---
layout: post
title: "CSS for Beginner: A Complete Guide to Grid"
author: "Serhii T."
categories: journal
tags: [css,grid]
image: 
---

The intention of this guide is to present the Grid concepts. More details you could find [here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout).

## PROPERTIES FOR THE PARENT(GRID CONTAINER)

#### display

Defines the element as a grid container and establishes a new grid formatting context for its contents.

Values:
- grid – generates a block-level grid
- inline-grid – generates an inline-level grid
```
.container {
  display: grid | inline-grid;
}
```

#### grid-template-columns | grid-template-rows

Defines the columns and rows of the grid with a space-separated list of values. The values represent the track size, and the space between them represents the grid line.

Values:
- track-size – can be a length, a percentage, or a fraction of the free space in the grid (using the fr unit)
- line-name – an arbitrary name of your choosing.
```
.container {
  grid-template-columns: ...  ...;
  /* e.g. 
      1fr 1fr
      minmax(10px, 1fr) 3fr
      repeat(5, 1fr)
      50px auto 100px 1fr
      [first] 40px
  */
  grid-template-rows: ... ...;
  /* e.g. 
      min-content 1fr min-content
      100px 1fr max-content
      [row1] 25% [row2] 75%
  */
}
```

**Note:** The fr unit allows you to set the size of a track as a fraction of the free space of the grid container. For example, this will set each item to one third the width of the grid container:
```
.container {
  grid-template-columns: 1fr 1fr 1fr;
}
```

#### grid-template-areas

Defines a grid template by referencing the names of the grid areas which are specified with the grid-area property. Repeating the name of a grid area causes the content to span those cells. A period signifies an empty cell. The syntax itself provides a visualization of the structure of the grid.

Values:
- grid-area-name – the name of a grid area specified with grid-area
- . – a period signifies an empty grid cell
- none – no grid areas are defined

```
.item-a {
  grid-area: header;
}
.item-b {
  grid-area: main;
}
.item-c {
  grid-area: sidebar;
}
.item-d {
  grid-area: footer;
}

.container {
  display: grid;
  grid-template-columns: 50px 50px 50px 50px;
  grid-template-rows: auto;
  grid-template-areas: 
    "header header header header"
    "main main . sidebar"
    "footer footer footer footer";
}
```

That’ll create a grid that’s four columns wide by three rows tall. The entire top row will be composed of the header area. The middle row will be composed of two main areas, one empty cell, and one sidebar area. The last row is all footer.

#### grid-template

A shorthand for setting grid-template-rows, grid-template-columns, and grid-template-areas in a single declaration.

Values:
- none – sets all three properties to their initial values.
- grid-template-rows / grid-template-columns – sets grid-template-columns and grid-template-rows to the specified values, respectively, and sets grid-template-areas to none.

#### column-gap | row-gap | grid-column-gap | grid-row-gap

Specifies the size of the grid lines. You can think of it like setting the width of the gutters between the columns/rows.

Values:
- line-size – a length value.

A shorthand for row-gap and column-gap is **gap**.
Values:
- grid-row-gap | grid-column-gap – length values.

#### justify-items

Aligns grid items along the inline (row) axis (as opposed to align-items which aligns along the block (column) axis). This value applies to all grid items inside the container.

Values:
- start – aligns items to be flush with the start edge of their cell
- end – aligns items to be flush with the end edge of their cell
- center – aligns items in the center of their cell
- stretch – fills the whole width of the cell (this is the default)
```
.container {
  justify-items: start | end | center | stretch;
}
```

#### align-items
Aligns grid items along the block (column) axis (as opposed to justify-items which aligns along the inline (row) axis). This value applies to all grid items inside the container.

Values:
- start – aligns items to be flush with the start edge of their cell
- end – aligns items to be flush with the end edge of their cell
- center – aligns items in the center of their cell
- stretch – fills the whole height of the cell (this is the default)
```
.container {
  align-items: start | end | center | stretch;
}
```

#### place-items
**place-items** sets both the _align-items_ and _justify-items_ properties in a single declaration.

Values:
- align-items / justify-items – The first value sets align-items, the second value justify-items. If the second value is omitted, the first value is assigned to both properties.

This can be very useful for super quick multi-directional centering:
```
.center {
  display: grid;
  place-items: center;
}
```

#### justify-content

Sometimes the total size of your grid might be less than the size of its grid container. This could happen if all of your grid items are sized with non-flexible units like px. In this case you can set the alignment of the grid within the grid container. This property aligns the grid along the inline (row) axis (as opposed to align-content which aligns the grid along the block (column) axis).

Values:
- start – aligns the grid to be flush with the start edge of the grid container
- end – aligns the grid to be flush with the end edge of the grid container
- center – aligns the grid in the center of the grid container
- stretch – resizes the grid items to allow the grid to fill the full width of the grid container
- space-around – places an even amount of space between each grid item, with half-sized spaces on the far ends
- space-between – places an even amount of space between each grid item, with no space at the far ends
- space-evenly – places an even amount of space between each grid item, including the far ends

#### align-content

This property aligns the grid along the block (column) axis (as opposed to justify-content which aligns the grid along the inline (row) axis).

Values:
- start – aligns the grid to be flush with the start edge of the grid container
- end – aligns the grid to be flush with the end edge of the grid container
- center – aligns the grid in the center of the grid container
- stretch – resizes the grid items to allow the grid to fill the full height of the grid container
- space-around – places an even amount of space between each grid item, with half-sized spaces on the far ends
- space-between – places an even amount of space between each grid item, with no space at the far ends
- space-evenly – places an even amount of space between each grid item, including the far ends

#### place-content

**place-content** sets both the _align-content_ and _justify-content_ properties in a single declaration.

Values:
- align-content / justify-content – The first value sets align-content, the second value justify-content. If the second value is omitted, the first value is assigned to both properties.

#### grid

A shorthand for setting all of the following properties in a single declaration: grid-template-rows, grid-template-columns, grid-template-areas, grid-auto-rows, grid-auto-columns, and grid-auto-flow (Note: You can only specify the explicit or the implicit grid properties in a single grid declaration).

The following two code blocks are equivalent:
```
.container {
  grid: 100px 300px / 3fr 1fr;
}

.container {
  grid-template-rows: 100px 300px;
  grid-template-columns: 3fr 1fr;
}
```

## PROPERTIES FOR THE CHILDREN (GRID ITEMS)

#### grid-column-start | grid-column-end | grid-row-start | grid-row-end

Determines a grid item’s location within the grid by referring to specific grid lines. grid-column-start/grid-row-start is the line where the item begins, and grid-column-end/grid-row-end is the line where the item ends.

Values:
- line – can be a number to refer to a numbered grid line, or a name to refer to a named grid line
- span number – the item will span across the provided number of grid tracks
- span name – the item will span across until it hits the next line with the provided name
- auto – indicates auto-placement, an automatic span, or a default span of one.

#### grid-column | grid-row

Shorthand for grid-column-start + grid-column-end, and grid-row-start + grid-row-end, respectively.
```
.item {
  grid-column: 3 / span 2;
  grid-row: third-line / 4;
}
```

#### grid-area

Gives an item a name so that it can be referenced by a template created with the grid-template-areas property. Alternatively, this property can be used as an even shorter shorthand for grid-row-start + grid-column-start + grid-row-end + grid-column-end.

#### justify-self
Aligns a grid item inside a cell along the inline (row) axis (as opposed to align-self which aligns along the block (column) axis). This value applies to a grid item inside a single cell.

Values:
- start – aligns the grid item to be flush with the start edge of the cell
- end – aligns the grid item to be flush with the end edge of the cell
- center – aligns the grid item in the center of the cell
- stretch – fills the whole width of the cell (this is the default)

#### align-self
Aligns a grid item inside a cell along the block (column) axis (as opposed to justify-self which aligns along the inline (row) axis). This value applies to the content inside a single grid item.

**place-self** sets both the align-self and justify-self properties in a single declaration. The first value sets align-self, the second value justify-self. If the second value is omitted, the first value is assigned to both properties.

## Special Units & Functions

#### fr units
They essentially mean “portion of the remaining space”. 
```
grid-template-columns: 1fr 3fr;
```
So a declaration like above means, loosely, 25% 75%. Except that those percentage values are much more firm than fractional units are. For example, if you added padding to those percentage-based columns, now you’ve broken 100% width (assuming a content-box box model). Fractional units also much more friendly in combination with other units.

#### Sizing Keywords
When sizing rows and columns, you can use all the lengths you are used to, like px, rem, %, etc, but you also have keywords:
- min-content: the minimum size of the content. Imagine a line of text like “The very long hotdog.”, the min-content is likely the width of the world “The”.
- max-content: the maximum size of the content. Imagine the sentence above, the max-content is the length of the whole sentence.
- auto: this keyword is a lot like fr units, except that they “lose” the fight in sizing against fr units when allocating the remaining space.
- fit-content: use the space available, but never less than min-content and never more than max-content.
- fractional units: see above.

#### Sizing Functions
The minmax() function does exactly what it seems like: it sets a minimum and maximum value for what the length is able to be. This is useful for in combination with relative units. Like you may want a column to be only able to shrink so far. This is extremely useful and probably what you want:
```
grid-template-columns: minmax(100px, 1fr) 3fr;
```

#### The repeat() Function and Keywords
The **repeat()** function can save some typing:
```
grid-template-columns:
  1fr 1fr 1fr 1fr 1fr 1fr 1fr 1fr;

/* easier: */
grid-template-columns:
  repeat(8, 1fr);

/* especially when: */
grid-template-columns:
  repeat(8, minmax(10px, 1fr);
```

But **repeat()** can get extra fancy when combined with keywords:
- auto-fill: Fit as many possible columns as possible on a row, even if they are empty.
- auto-fit: Fit whatever columns there are into the space. Prefer expanding columns to fill space rather than empty columns.

This bears the most famous snippet in all of CSS Grid:
```
grid-template-columns: 
  repeat(auto-fit, minmax(250px, 1fr));
```

The difference between the keywords is spelled out in detail [here](https://sergeytocarchuk.github.io/css-grid-auto-fill-vs-auto-fit).

### Resources:
- learning Grid Properties has been gamified in [GRID GARDEN](https://cssgridgarden.com/#ru)
