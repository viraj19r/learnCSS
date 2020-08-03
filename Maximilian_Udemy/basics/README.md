# Notes
Cascading style sheets(CSS) is used to style pages(Latest version of CSS is CSS3)
### what is viewport
visible part of our app in browser window
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
#### Gradient(linear or radial)
 - linear gradient
   - `background-image: linear-gradient(to bottom or left bottom(means diagonally) or 30 degrees(angle),red,blue)` first argument is direction of the gradient and if we leave it then the other all arguments will be color(among which the gradient occurs) 
   - or we can also define percentage of each color along with it(red70%,yellow5%,green25%)

 - radial gradient(that starts with certain shapes)
   - `background-image: radial-gradient()` default is the ellipse shape.
   - in its first argument we can define shapes(circle,etc) and also their places(circle at top, circle at top left, circle at 20% 30%) and also size(circle 20px at 20% 30%),(circle farthest-size(or closest size) at 20% 30%)

#### Stacking Multiple backgrounds
 
 - `background: url(..) url(..) linear-gradient() url(..) red  .........`
 - image will be always prior to any color and gradient

#### Filter css property
  -  it lets us  apply graphical effects like blurring or color shifting to an element

  -  `filter: value`
  -  value
    - url()
    - blur(5px)
    - contrast(200%)
    - grayscale(80%);  
    - hue-rotate(90deg)
    - drop-shadow(16px 16px 0 red) 
    - invert(75%)
    - opacity(25%)
    - saturate(34%)
    - sepia(23%)
  - we can also use multiple filters by separating them with a white space
  - global values for `filter:inherit`,`filter:initial`,`filter:unset`

#### SVG 
we can add svg(their designed codes are available) in our html page and style them using the css
*  background image is better than <img> when we want to use more style.

## **Sizes** and **Units**
- we should always design our product to be browser friendly(like when we zoom in or out or we change the browser font setting then our website fonts should be changed, that will not change if we use the percentage units or the unit that not that is not capable of doing it). In the scenario like that of font, we need to be very choosy about our unit selection and what is our requirement.

| Units           | short notation used in css |
| --------------- | -------------------------- |
| pixel           | px                         |
| percentage      | %                          |
| root em         | rem                        |
| em              | em                         |
| viewport height | vh                         |
| viewport width  | vw                         |

* Where we use these units ?
 - font-size
 - padding
 - border
 - margin
 - width
 - height
 - top
 - bottom 
 - left
 - right

| Absolute lengths                              | viewport lengths           | font-relative lengths  |
| --------------------------------------------- | -------------------------- | ---------------------- |
| mostly ignore user settings(browser settings) | adjust to current viewport | adjust to default size |
| **px**                                        | **vh**                     | **rem**                |
| cm                                            | vw                         | **em**                 |
| mm                                            | vmin or vmax               | ..                     |
|                                               | percentage(%)              | percentage(%)          |

##### how does the percentage unit work and what does it refer to
percentage value is decided on the basis of the container element of a current element(or we can say that the percentage value is taken in the reference of the container element), normally the container of an element is its parent element.
* But in the case of `position:fixed` the container element becomes the **viewport**.
* In case of `position:absolute` ,then the container element becomes the **ancestor's content + padding**. 
* In case of `position:relative(or static)`, then the container element becomes the **ancestor's content** only
* In case of height(and if the position is relative) we also need to define the height in the container element to be 100%(for ex when we create an backdrop inside a body element using div tag then we also need to define the height for body element and html element). Otherwise the the given height to our tag will not work.

- We can define `min-width/height` and `max-width/height` for our element (like as image) so that the when we expand or shorten our container then the element will increase or decrease up to certain limit(as decided using min or max).

- we use `em` and `rem` values for the font size so that when we change browsers setting for the fonts then the font of our page should also change.
  - when we use `em` then it takes the value from its ancestor or sibling to multiply with the em value which might change according to the window size. Instead of `em`, `rem` always takes the reference of default browser value which is `16px` for the root element(html element). So we always use the `rem`. we use the `em` value only for the elements that are separate and independent. 
- we can also use the `vh` or `vw` units for the height and width in place of `%`, both works same as `vh` and `vw` are also relative to the viewport

 ##### Windows, Viewport Units & Scroll bars
After adding vw , you probably saw that the scroll bars appeared in case you are working on Windows. This happens as using vw  on Windows does not include the scroll bars - `vw: 100`  is  equal to 100% of the viewport width`+` the scroll bars. On the Mac this is not an issue, but when using Windows it is as the scroll bars are displayed by default.

In case you don't want to display these scroll bars, you can use one of these solutions:

- Use width: 100%  instead of vw: 100

- Add overflow-x: hidden;  to the body selector in the shared.css file to hide the horizontal scrollbar (or overflow-y: hidden  to hide the vertical scrollbar)

Alternatively you could also use the ::-webkit-scrollbar pseudo element.
```
 body: :-webkit-scrollbar {
    width: 0
}
```

##### Recommended units to be used according to the properties
|Property|Recommendation|
|font-size(of root element)|`%`|
|font-size|`rem`,`em`(only use for the children not for parent and others)|
|padding and margin|`rem`|
|border|`px`|
|width and height|`%`,`vw`,`vh`|
|top and bottom,left and right|`%`|













