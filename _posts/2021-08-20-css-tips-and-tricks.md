---
layout: post
title: "CSS: Few Concepts for Beginner"
author: "Serhii T."
categories: journal
tags: [css]
image: 
---

Here we will talk about:
- The Box Model (e.g. box-sizing, height, width, margin, padding)
- Layout (e.g. display)
- Document Flow and Positioning (e.g. position, top, left, etc.)

### THE BOX MODEL

When you consider the size of an element (i.e. its height and width), there are two different models by which to measure this and you can adjust this with the box-sizing property:
- _box-sizing: content-box_ (browser default)
The size of an element only includes its content, and not its padding or border.

- _box-sizing: border-box_
The size of an element is inclusive of its padding and border. When you set width: 100% with content-box, the content will be 100% of the width of the parent element, but any borders and padding will make the element even wider.

_border-box_ makes a lot more sense, and I find it much easier to reason about. To apply border-box to all elements on the page, make sure you have something like this snippet in your stylesheet (a lot of CSS resets will include this anyway):

```
CSS
*, ::before, ::after {
  box-sizing: border-box;
}
```

Going forward, I'm only going to be considering border-box.

- _margin_ values sometimes collapse with an adjacent element's margin, taking the maximum of the margins between them rather than the combination of both. The rules around this can be somewhat complex, and MDN has a document describing them: [Mastering margin collapsing](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
- _margin_ and explicit _width/height_ don't work on inline content
- _margin_ is not applicable to table cells

### LAYOUT

Elements are usually laid out in the document in the order that they appear in the markup. The display property controls how an element and/or its children are laid out. You can read about display in more detail at [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/display):
- _display: inline_ allows content to flow kind of like text and to fit with other inline content, sort of like tetris pieces
- _display: block_ means the element effectively behaves like a rectangle containing all of its children that grows in height to fit content (width is 100% of the parent content box by default). Effectively, line breaks are inserted before and after the element.
- _display: inline-block_ is like a mixture of both inline and block. Its contents will be contained within a rectangle, but that rectangle can be laid out as part of inline content.
- _display: flex_ and _display: grid_ are more advanced layout algorithms for arranging children according to certain rules. These are the bread and butter of building flexible, responsive layouts and are well-worth learning about in more depth. Learning these has been gamified in [Flexbox Froggy](https://flexboxfroggy.com/#ru) and [Grid Garden](https://cssgridgarden.com/#ru).

### DOCUMENT FLOW AND POSITIONING

The position property affects how elements are positioned with respect to the flow of the document in combination with positioning properties (top, left, right, bottom, etc.).

- elements are _position: static_ by default, which means that positioning properties have no effect on the position of the element and the element is laid out normally. Statically positioned elements also do not have their own stacking context, which means that setting z-index will also have no effect.
- _position: relative_ is like position static, except that top, left, and other positioning properties act like an offset of where the element should be visually laid out (although sibling and ancestor elements will behave as though it is still in the original position).
- _position: absolute_ takes the element out of the flow of the document and ancestors/siblings will be laid out as if the element were not present. Positioning properties specify offsets of where the element should be visually laid out relative to the nearest non-static parent. You can add _position: relative_ to an ancestor to use it as the anchor point for an element with position: absolute.
- _position: fixed_ along with positioning properties means that the element is removed from the normal flow of the document and instead laid out relative to the viewport. If positioning properties are specified, they will ensure the element is laid out always with that offset to the viewport (i.e. they appear fixed in place and don’t move, even when scrolling).
- _position: sticky_ is a bit more complex, but you can think about it as a hybrid of position: relative and position: fixed. You can read more about the exact mechanism at [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/position#sticky).