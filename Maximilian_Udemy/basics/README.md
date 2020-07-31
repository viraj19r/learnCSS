# Notes
Cascading style sheets(CSS) is used to style pages(Latest version of CSS is CSS3)

### selectors in css
- element selector(elements name)-- select all the elements present in the page with the name
- class selector(.) -- more than one element can have same class
- universal selector(*) -- selects all the elements inside the page
- id selector(#)-- id should be unique for every element
- attribute selector([attribute name])-- select all the elements having same attributes

### Specificity(applying order for css selectors)[lowest to highest]
- <tag> and ::pseudo-element selector
- .class, ::pseudo-class and [attribute]selectors
- #id selectors
- inline styles

#### Inheritance 
Inheriting the styles of parent elements. But have low priority then the child(original) one.
#### Combinators
Allows us to combine multiple selectors and then it will also create higher specificity
Types
- Adjacent combinator(+) ---- div + p {}  applied to adjacent sibling(which is just next to it or which share same parent, which follows it)
- General Sibling(~) ---- div ~ p {}  it selects all siblings which are on the same level no matter is just next to it
- child combinator(>) ---- div > p{}   applied to direct child
- Descendant( ) ---- div p {}  applied to all children's with the same selector, no matter how much deeper our children is

### Margin Collapsing
When working with margins, you can get unexpected results. 

Why are two adjacent elements sharing one margin even though each element has its own one?
Why does a parent element (e.g. `<section>`  as in the videos) suddenly take on the margin of the child element e.g. `<h1>`

There, three base cases are described:

- Adjacent siblings which both have margins
- A parent which holds one or more child elements where the first and/ or last (or the only) child has margins
- An element without content, padding, border and height
Let's explore these cases:

1. Adjacent Siblings

In this case, the first element might have a margin of 10px  (on all sides let's say) and the second one has 5px  (or 20px  - the values don't matter).

CSS will collapse the margins and only add the bigger one between the elements. So if we got margins of 10px  and 5px , a 10px  margin would be added between the elements?

2. A parent with children that have a margin

To be precise, the first and/ or last or the only child has to have margins (top and/ or bottom). In that case, the parent elements margin will collapse with the child element(s)' margins. Again, the bigger margin wins and will be applied to the parent element.

If the parent element has padding, inline content (other than the child elements) or a border, this behavior should not occur, the child margin will instead be added to the content of the wrapping parent element.

3. An empty element with margins

This case probably doesn't occur that often but if you got an element with no content, no padding, no border and no height, then the top and bottom margin will be merged into one single margin. Again, the bigger one wins.

#### Shorthand Properties
combine values of multiple properties in a single properties(the shorthand properties).
Like
- margin for margin-top, margin-right, margin-bottom,margin-left
- border for border-width, border-style, border-color.

#### display: none vs visibility: hidden
We had a look at display: none;  - this value removes the element to which you apply it from the document flow. This means that the element is not visible and it also doesn't "block its position". Other elements can (and will) take its place instead.

There is an alternative to that though.

If you only want to hide an element but you want to keep its place (i.e. other elements don't fill the empty spot), you can use visibility: hidden; 

Here's a visual example:

``` .box-1 {
    display: none;
}
 
.box-2 {
    display: inline-block;
}
```
Will render:

`x`  

where `x`  has the class box-2 . The first element just isn't displayed. It's still part of the DOM though, you can still access it via JavaScript for example.

Here's an example for visibility: hidden :

``` .box-1 {
    visibility: hidden;
}
 
.box-2 {
    display: inline-block;
}
```
Will render:

`_x`

where `_`  simply is an empty spot and `x`  has the class box-2 .

The element is only invisible, it's not removed from the document flow and of course also not from the DOM.

#### pseudo classes and pseudo elements
pseudo class allow us to define style of a **special state** of an element`:class name`
pseudo elements allow us to define the style of a **specific part**  of a element`::element name`

- If we use `!important` after any property's value ,then that property will override all the existing properties on that element. It is highly recommended not to use this.
- `:not()` (It is a pseudo class)is used to exclude anything(the part which will be passed as argument will not be effected by the properties that we are going to set).

### Positioning elements(position:static(default value))

`property values:` `static`,`absolute`,`relative`,`fixed`,`sticky`(new value).
- `z-index`
stacking context
we can apply positioning properties to both inline and block elements

### Background image and image
- `background-image:url();` sets the background image
- `background-size: value:` sets the background size of the elements(we can also specify both height and width)
  - value
    - `contain` - whole image will be contained in the image container
    - `cover`- the image will cover the whole area of the viewport or window.
    - `%`- we can specify values also in percentage
    - `120px 110px` - we can set both height and width. 

- `background-position:value;` - if we use value in `%` then the image will shift inside the container but if we use the value in `px` then the image will shift as per the given value.
  - value
    - `center`- center the image
    - `left top`- image will be positioned towards top left(and also we can use all the possible combinations).instead of using we can also use the `%` values here
- `background-repeat: value;` - controls whether the image should repeat or not
  - value
    - `no-repeat` - no repetition of image
    - `repeat-x` - image will repeat in x-direction
    - `repeat-y` - image will repeat in y-direction 
- `background-origin: value;` - help us to manage the background image with border
  - value
    - `border-box` - border will be contained inside the image not outside the image
    - `padding-box` - default behaviour  
    - `content-box` - image will be inside the content box
- `background-clip` - we will define how the image will actually clipped with border same property values as of background-origin property has.
- `background-attachment` - define how the scrolling will behave in content box where background image is set
  - value
    - `scroll` - image will be able to scroll inside the container
    - `local` - 
    - `fixed` - image will not be fixed to the content-container but for the viewport     
- ShortHand syntax for background properties
    `background: background-image background-position/background-size background-repeat background-origin background-clip;` (if the values of background-origin and background-clip are same then we can replace these two values with only one value).
   #### Styling Images 





