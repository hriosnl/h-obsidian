## Box-sizing the hell out of it

Instead of having to remember to swap box-sizing on every layout element, we can set it as the default value for all elements with this handy code snippet:
`\*,
\*::before,
\*::after {
box-sizing: border-box;
}`

It's super important that you never apply the following CSS, removing the outline:
`
button {
  outline: none;
}
`
## Margins
It's easy to fall into the trap of thinking that **margin** is exclusively about changing the selected element's position. Really, though, it's about changing _the gap between elements_.

Negative margins can take some element *out of its parent container*


## Directions in Flow Layout
Block elements don't share
Inline elements can line-wrap

## Height and Width
Broadly speaking, there are two kinds of values we can specify for `width`:

1. Measurements (100%, 200px, 5rem)    
2. Keywords (auto, fit-content)

`width` default is auto, while `height` is close to min-content

`height` tends to look "down" the tree, to determine its size based on the natural size of its contents, while `width` tends to look "up" the tree, basing its size on the space made available by the parent.

## Margin Collapse
Margin collapse is _unique to [Flow layout](https://courses.joshwcomeau.com/css-for-js/01-rendering-logic-1/09-flow-layout)_. If you have children inside a `display: flex` parent, those children's margins will never collapse.

**Margins must be touching in order for them to collapse.**

---
## Positioned Layout

The defining feature of positioned layout is that items can overlap. The Flow Layout algorithm tries very hard to make sure that multiple elements never occupy the same pixels.

##### Position: relative -  _relative to its natural position._
1. Constrains certain children
2. Enables additional CSS properties to be used.

Unlike margins, **`position` doesn't impact layout.**

relative positioning can be applied to _both block and inline elements_.

##### Position: absolute
Absolutely-positioned elements are **adjusted based on their container,** not based on their in-flow position.

When we set something to be `position: absolute`, we **pull it out of flow.**

Absolutely positioned elements are *strictly compliant*.

## Containing Blocks
A containing block is a rectangle that forms the bounds of the element's container.

**Absolute elements can only be contained by _other_ elements using Positioned layout**

padding is used in Flow layout calculations, and absolute elements are taken out-of-flow. Those rules don't apply.

## Stacking Contexts
As a general rule, **positioned elements will always render on top of non-positioned ones**. We can think of it as a two-stage process: first, all of the non-positioned elements are rendered (everything using Flow, Flexbox, Grid…). Next, all of the positioned elements are rendered on top (relative, absolute, fixed, sticky).

`z-index` only works with positioned elements. It will have no effect on an element being rendered in Flow layout.

### The isolation property

Instead of adding `position: relative; z-index: 1;` to our `.pricing` selector, we can do this:

.pricing {
  isolation: isolate;
}

The `isolation` property does precisely 1 thing: creates a stacking context.

## Fixed Positioning

If a parent or grandparent uses the `transform` property, it becomes the containing block for the fixed element, essentially transforming it into an absolutely-positioned element or **transformed parents can't have fixed children**.

Also, the `will-change: transform` declaration has the same effect

## Overflow

`overflow: auto` is the ideal behaviour when we know an element _might_ overflow

Adding *detailed comments when using overflow: hidden* is absolutely critical. Otherwise, you'll never remember why you set the property.

### Horizontal Overflow
`white-space` is a property that lets us tweak how words and other inline/inline-block elements wrap. By setting it to `nowrap`, we instruct the container to never break lines. That, in tandem with `overflow: auto`, allows us to achieve a horizontally-scrollable element.

## Sticky Positioning

An often-overlooked aspect of `position: sticky` is that the element will never follow the scroll outside of its parent container. Sticky elements only stick while their container is in view.

Sticky elements are like relative or static elements in this regard; they're laid out in-flow. They take up real space, and that space remains taken even when the element is stuck to an edge during scrolling.

---
# Flexbox

align-self - for secondary/cross axis

in a flexbox, width and height are hypothetical, flexbox does not respect it when there is no space left--but there's a minimum width and height, and that probably is the text content

flex-basis, the size of the dimension in main axis i.e. width or height

flex-grow overrides flex-basis

flex-shrink and flex-grow defines *how fast* the element should shrink or grow

There are two important sizes when dealing with Flexbox: the _minimum content size_, and the _hypothetical size_.

`flex-basis` can't scale an element below its minimum content size, but `width` can

Use the `flex` shorthand, e.g. flex: 1 0 500px;

combine `flex-wrap: wrap` with flex-basis (and max-width)

**Content vs Item**
Content - the whole group
Item - the individual item

### Positioned Flex children
When there is a conflict between layout modes, **positioned layout always wins.**
Relative position is *compatible*, the element will be laid out first as flex item then positioning (top, left, etc)

---
# Animation

transform: scale, scale even the descendants unlike changing the width and height
This reveals an important truth about transforms: **elements are flattened into a texture**


----
# Grid Layout

display: grid
grid-template-columns: repeat(3, 120px)
grid-template-rows: 1fr 1fr
justify-content: space-between
align-content: center
justify-items: start
align-items: end

align-self: center
justify-self: end

### 40 Tracks and Lines
