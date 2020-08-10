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
- [Advanced attribute selectors](https://www.w3schools.com/css/css_attribute_selectors.asp#:~:text=CSS%20%5Battribute%5E%3D%22value,to%20be%20a%20whole%20word!)

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
### Box shadow
The `box-shadow` property applies one or more shadows to an element.

The `box-shadow` property takes values for
```
offset-x (how far to push the shadow horizontally from the element),
offset-y (how far to push the shadow vertically from the element),
blur-radius,
spread-radius and
color, in that order.
```
The `blur-radius` and `spread-radius` values are optional.

Multiple box-shadows can be created by using commas to separate properties of each `box-shadow` element.
`box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);`
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
| Property                      | Recommendation                                                  |
| ----------------------------- | --------------------------------------------------------------- |
| font-size(of root element)    | `%`                                                             |
| font-size                     | `rem`,`em`(only use for the children not for parent and others) |
| padding and margin            | `rem`                                                           |
| border                        | `px`                                                            |
| width and height              | `%`,`vw`,`vh`                                                   |
| top and bottom,left and right | `%`                                                             |

## Responsive web design

  > ##### Hardware pixel(device pixels) vs Software pixels(css pixels)
  > The pixels of our device are hardware pixels and the pixels that we assign through css are software pixels.

Basically we have two tools to apply responsive web design

| Viewport(html meta tag)                            | Media queries(css)                            |
| -------------------------------------------------- | --------------------------------------------- |
| required to adjust our site to the device viewport | allow us to change size depending on the size |
| No design changes are allowed                      | these changes are defined by us               |

 #### Viewport meta tag
`<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=2.0, minimum-scale=1.0,user-scalable=yes"> `

Here first `name` attribute tells the meta tag that it is referring to the device's viewport second `content` attribute tells that the site's size should be equal to the device size/viewport and the third attribute `initial-scale` manages the page zoom(1 is default value: no zoom), user-scalable ensures that the user can do zoom in and out, `maximum-scale` ensures the maximum zoom value, `minimum-scale=1.0` ensures the minimum zoom value

>We usually design website to be ***Mobile first***, means we design the website giving the first priority to the mobile(responsive towards mobile) , because today most of the user uses mobiles to open the websites. So we will always design our website for mobile and then make it responsive for the laptops and tablets

#### Media Queries
- First of all we add the meta(viewport) tag to all our existing html pages.
- 
Syntax: 
```
@media (if given condition is true){
  css selector {
    css properties values
  }
}
```
- If our css code is for the mobile and we want the media  queries for desktop then we use
   ```
   @media(min-width: 40rem){ 
   css code...
   }
   ```
  - if width is greater than or equal to 40rem then condition is true and proceed.
- If our css code is for the desktop and we want the media  queries for mobile then we use
  ```
   @media(max-width: 40rem){ 
   css code...
   }
  ```
  - if width is lesser than or equal to 40rem then condition is true and proceed
- media query(working with logical operators)
  - using 'and' 
   `@media (min-width: 40rem) and (orientation:portrait)`
   `@media (min-width: 40rem) and (min-height: 60rem)`
  - using 'or' 
   `@media (min-width: 40rem), (orientation:landscape)`
   `@media (min-width: 40rem), (min-height: 60rem)`

  #### Styling forms
  - we can use the `:invalid` `:valid`pseudo classes to check our input in forms and design the form input element differently(like giving the red color to input box). And now the browser auto checks the input and apply the pseudo class to it(browser basically compares with the type attribute of our input tag).
  - we can also add `required` attribute to our input tags, in this case the input should be mandatory otherwise the invalid pseudo class will be applied.
  - we can use `:focus` pseudo class to change the style of the input box like outline and border when the box is active(when we are going to input something in it or clicked on it.

#### Texts and Fonts
Generic families vs font families
Generic families includes some type of font families that further contain many types of fonts(like as **serif** --- Times New Roman ,Georgia,etc; **sans-serif** --- Helvetica,Verdana,etc;**cursive**--- Brush Script , Mistral,etc;**monospace** --- Courier New, Lucida Bright,etc;**fantasy**).

Font Properties
- `font-variant` can set different variants of font
- `font-stretch` stretching of the letters
- `letter-spacing` defines space between the letters
- `white-space` if we set it to `no-wrap` then the entire text will be displayed in the one line and if we set it to `pre` then text will be displayed as in the html file and we also have `pre-wrap` ,`pre-line`(all lines will be filled as much possible).
- `line-height` defines the height of a line(values are normal,numerical values(recommended) = 1,2,3... and percentages = 100%,200%)
- `text-decoration` values = underline,overline,line-through dotted,wavy(extra specification) red(color specification)
- `text-shadow` value = 5px(offset x-axis) 5px(offset to the y-axis) 2px(blur) gray(color)
- Shorthand property font: font-style font-variant font-weight font-size/line-height font-family
- `font-display` and loading performance
  - values;
  - swap --Gives the font face an extremely small block period and an infinite swap period.
  - block -- Gives the font face a short block period and an infinite swap period.
  - fallback--Gives the font face an extremely small block period and a short swap period.
  - optional--Gives the font face an extremely small block period and no swap period.
  - auto (default) 

- The `text-transform` property in CSS is used to change the appearance of text. It's a convenient way to make sure text on a webpage appears consistently, without having to change the text content of the actual HTML elements.

The following table shows how the different `text-transform` values change the example text "Transform me".

| Value      | Result                                               |
| ---------- | ---------------------------------------------------- |
| lowercase  | "transform me"                                       |
| uppercase  | "TRANSFORM ME"                                       |
| capitalize | "Transform Me"                                       |
| initial    | Use the default value                                |
| inherit    | Use the text-transform value from the parent element |
| none       | Default: Use the original text                       |


## Flexbox 
- It allow us to change the way our elements are displayed.
- To create a **flex container** we will give the value flex to the display property
`display: flex;` , and the children's inside the flex container are **flex items**
- Once we have created the flexbox we can now apply following properties
  - Properties for flex container(parent)-- `flex-flow`-shorthand for(`flex-direction`,`flex-wrap`),`justify-content`,`align-content`,`align-items` ,
  - Properties for flex items(children)-- `order`,`flex`,`align-self`
  #### Main axis vs cross axis
  - if we create a flexbox with `flex-direction;row` then the main axis will be from left(top) to right and the cross axis will be from top(left) to bottom
  - if we create a flexbox with `flex-direction;row-reverse` then the main axis will be from right(top) to left and the cross axis will be from top(right) to bottom
  - if we create a flexbox with `flex-direction;column` then the main axis will be from top(left) to bottom and the cross axis will be from left(top) to right
  - if we create a flexbox with `flex-direction;column-reverse` then the main axis will be from bottom(left) to top and the cross axis will be from left(bottom) to right

- `justify-content` works along main axis and `align-items` work along cross axis
- we can use `align-content` to align content along the cross axis(all content inside the flex container will be aligned as per the property value)

>Flexbox and the Z-Index
>In the position module we learned that adding the z-index  to an element only has an  >effect, if the position  property with a value different from static  was applied to this >element.
>One exception from this behaviour is flexbox: Applying the z-index  to flex-items (so the >elements inside of the flex-container) will change the order of these items even if no >position  property was applied.

- Flex items properties
  - `order:0` it decides the order of the flex item among all flex items
  - `align-self:0` (0 is default value)we can also align particular items among all flex items using it
  - `flex` properties for items
    - `flex-grow:0`(default value) now if we increase its value for flex item and then if we increase the size of our window/viewport then this item(size) will also increase/grow(can say) using the extra space available. With the help of number as values, we can set/priorities which element will grow more or less. if we use it with `flex-wrap:wrap;` then it will change the line and occupies the full space in the next available line/space.
    - `flex-shrink:0` (default value) its opposite of flex-grow, it shrinks the flex item when the window size shrinks.If we specify greater values then they also tells the the flex items how much should it shrink comparative to other items.
    - `flex-basis:1`(default value- allow to shrink as it is 1) It basically defines the size of the flex item depending on the main axis(along the flex-direction).we can also use `%` values as we used for width and height.
      - if our main axis is from left to right then it will define and set width of flex item
      - if our main axis is from top to bottom then it will define and set the height of the flex item 
      - flex-basis always override the width and height properties
    - flex shorthand property `flex:flex-grow flex-shrink flex-basis;`

## Grid
- firefox has better developer tools for css grid than chrome's developer tools
- we can add grid container as `display: grid`
  - `grid-template-columns: 200px 300px 20%(of surrounding container) 1fr(fraction)...;` as much columns as we want, fraction takes the remaining space. If we sets the units to `auto` then it takes the space as much as the element requires only in the case when height and width properties are not defines, if they are defined then the element will cover all the remaining space.
  `grid-template-rows: 5rem 2rem ....;`


  - positioning child elements in a row(using some properties for containers items/child)
    -  we can set for the elements from where to start and where to end using the `grid-column-start:` and `grid-column-end:`,`grid-row-start` and `grid-row-end`properties.
    -  To occupy the whole columns and rows, we use `grid-column-end: span 2(as much as we want);` and `grid-row-end: span 2;`to span two elements in one
    -  to cover the whole line we can also use negative values such as `grid-row-end: -1;`

  - To create columns and row of same sizes we can use `repeat()` method`grid-template-columns:repeat(4, 25%)` first argument is for no of times it should repeat and second will be the size of the row of column. we can pass multiple second arguments, if we do so then the arguments passed will be considered as the sizes and they will be used as many times repetitively as we specify with the first argument. 
  - we can also set minimum and maximum heights and width for the respective rows and columns using the `minmax()` function as for row we can set height
    - `grid-template-row: 5rem minmax(10px 200px)`; 


- we can name row and column lines also by simply adding the names in square brackets as `grid-template-row:[row-1-start] 5rem [row-1-end row-2-start]minmax(10px 200px)` , we can also give multiple names to the lines by separating the names with a space.And now we can specify these names in the `grid-row-start`  and `grid-row-end` properties to grid the elements as we need. If we are using the repeat property to make rows and columns then we can give a general name to them(like as col-start/end or row-start/end) and later access them by adding a number(which is the no of that line from start) after general name with a space.


- Shorthand for `grid-column-start:1;` and `grid-column-end:-1;` is `grid-column:1/-1;` and same for `grid-row-start:1`  and `grid-row-end:-1` is `grid-row:1/-1;`. There is also and property named `grid-area` which is shorthand for all above four properties as `grid-area: grid-row-start/grid-row-start/grid-row-end/grid-column-end;`


- `grid-column-gap` and `grid-row-gap` allow us to define the gaps between columns and rows
- shorthand for gap is `grid-gap:grid-row-gap grid-column-gap;`
  
- there is a method `fit-content(8px)` now the content will be fit in 8px, we can use this method inside the `grid-template-rows` and `grid-template-columns` whenever required.


##### Named template areas in grid
we will define the `grid-template-area` in the element where we use the `display:grid`
and then later we use these defined areas in `grid-area` properties of grid items to arrange them.

- we can also position grid items by using the property`justify-items: center;`(for positioning inside the row) other values: `start`,`end`,`stretch`
- justify for x-axis and align for y-axis
- To position in the columns `align-items: center;`(other values;`start`,`end`,`stretch`)
- To position the entire grid and its content(grid items) `justify-content:center;` and `align-content: start;` 
- To position elements(grid item) individually we go to the element selector and use `justify-self: center;` property
  

- For responsive web design we need to add media queries with more rows in the grid
- if we have a blog like page where new blogs are added then in this case we can add a **autoflow** properties to the grid like `grid-auto-rows:auto` and there we can set the size of rows which will be created. and we can add `grid-auto-flow: column(or row) dense` in this case the new item will be added along the column and flow of the page will also be along the column. these are part of implicit grid. we can also add `dense` here so that if a item occupies a double row or column then an another item will get that place.


- the grid which we define are explicit grids and the grids which is added by user dynamically or any other method then the grid is called implicit grid .In case like that where the rows and columns are added dynamically we can use `auto-fill` inside the `repeat()` method in place of where we define the no of rows and columns and we can also use `auto-fit ` which will then also centers the items and if there is not space it will also put them in new line and fit inside the page, this is good for the case when we don't have enough items to fill in the page

> * we use grids when we need 2 dimensional positioning and flexbox when only needed 1 dimensional positioning


### Transforming CSS elements
- We transform the element using the `transform: rotateZ(45deg);`property 
- we can change the origin using `transform-origin: center;`(default value)
- we can use `translateX()` and `translateY()` function as value of `transform` property to move element right or left(left and right along the axis of the element which is transformed)
- we can use `skewX()` and `skewY()` function as value of `transform` property to skew elements at some angle or we can use shorthand `skew(value for x,value for y)`
- Along with skew we can also use `scaleX()` and `scaleY()` which will increase the size of the element along the defined axis
- we can also transform 3d using the `rotateX() rotateY() rotate()` function as a value of the transform element. we can use `perspective()` function to see the rotation as it gives clear visualization to us for the 3d transformation
- in 3d transformation we can also use `translateZ()` to translate along z-axis
- we can preserve the value of the 3d rotation using the `transform-style: preserve-3d;`
- To hide the back face of an element we use `backface-visibility:  hidden;`

#### Transition 
 `transition` property is used for the transition of a element, as a value of this property we can use transform,the property that will be effected(ex- width), opacity,etc
 
`transition: WHAT DURATION DELAY TIMING-FUNCTION; `
Example:
`transition: opacity 200ms 1s ease-out; `
Can be translated to: "Animate any changes in the opacity  property (for the element to which the transition  property is applied) over a duration of 200ms. Start fast and end slow, also make sure to wait 1s before you start".

Instead of this shorthand, we can also specify the four individual properties:

1. [transition-property](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-property) => `transition-property: opacity; `

2. [transition-duration](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-duration) => `transition-duration: 200ms;` 

3. [transition-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-timing-function) => `transition-timing-function: ease-out;` 

Possible timing function values are: ease-out , ease-in , linear , cubic-bezier()  and a couple of others.

4. [ transition-delay](https://developer.mozilla.org/en-US/docs/Web/CSS/transition-delay) => `transition-delay: 1s;`

#### Animation

- we can say animation as transition++. Transition only defines effect for only initial and final point but animation can define effect for multiple phases using the `@keyframe`
- `animation: NAME DURATION DELAY TIMING-FUNCTION ITERATION DIRECTION FILL-MODE PLAY-STATE;`

Example:
`animation: wiggle 200ms 1s ease-out 8 alternate forwards running; `
Can be translated to: "Play the wiggle keyframe set (animation) over a duration of 200ms. Between two keyframes start fast and end slow, also make sure to wait 1s before you start. Play 8 animations and alternate after each animation. Once you're done, keep the final value applied to the element. Oh, and you should be playing the animation - not pausing." 

Instead of this shorthand, we can also specify the individual properties:

1. [animation-name  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-name) => animation-name: wiggle; 

2. [animation-duration  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-duration) => `animation-duration: 200ms;` 

3. [animation-timing-function ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function) => `animation-timing-function: ease-out;` 

Possible timing function values are: ease-out , ease-in , linear , cubic-bezier()  and a couple of others. See the above link for more details.

4. [animation-delay  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-delay) => `animation-delay: 1s;` 

5. [animation-iteration-count  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-iteration-count) => `animation-iteration-count: 8; `

6. [animation-direction  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-direction) => `animation-direction: alternate;` 

7. [animation-fill-mode  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode) => `animation-fill-mode: forwards;` 

8. [animation-play-state  ](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state) => `animation-play-state: running;` 

- we can use `@supports (display: grid){}` to check whether our code supports the the functionality, if not the code inside the curly braces will not run
- In case any property is not supported then we can specify another with the help of the css variables
- CSS frameworks
  - bootstrap - component framework
  - tailwind - utility framework

#### SASS
sass/scss is super set for the css which contain more feature than the css to make everything easy and clear. sass should be converted in the css because browser's only understand css.
- We can define reusable code with sass
- // is used in sass for commenting
- if we name our file with .sass then we must not use the curly braces and semi colons, because they are not supported in sass but we must use the indentation
- if we name our file with .scss then we can use curly braces and semi colons
- if we want to define properties for any child element then it can be defined without using the combinator, we can simply put the child's selector inside the parent selector by using the normal syntax we use for selecting the elements but now inside the parents selectors body.


- nesting the properties in sass
   - example- we have defined the properties as `flex-direction: column;` `flex-wrap: nowrap`
   - we can using nesting as ` flex: { direction: column; wrap:nowrap;} `


- variable in sass allows us to define a certain value and reuse it around our code (variable should be defined at the top of the file so that it can be used everywhere)
   - declaring a variable for color(which will be used max in our code) `$main-color: red;`.we can store any of the property value in variables.
   - lists and maps can also be stored in variables(list- that store more than one value, like when we define box shadow, there are many values),(map is a list in which each item has name by which we can access it. )
     - storing list in variable `$border-default: 0.05rem solid black;`
     - storing map in variable `$colors: (main: red, secondary: green, tertiary: yellow)`
       - accessing map value by map-get method as `map-get($colors,main)`


- there are many built in functions in sass that makes styling easier
- we can do some arithmetic's with sass like with units `padding: $size-default * 3;`(for sass $size-default = 1rem) now it will calculate it as 3rem
- In sass we can nest media queries in the element for which we created them
- Inheritance in sass - the code which is repeated in different selectors, we will write a class selector and write down the repeating code(also media queries) in it and inherit that newly written class using `@extends ` followed by the class name inside the selector where we need to inherit.
- Mixins are functions that we create to shorten the code. we can define mixin as follows
    ```
       @mixin display-flex($passAnArgument){
         display: flex;
         display: -webkit-flex;
         size: $passAnArgument
         @content
       }
    ```   
    And now we can use it where we want as 
    `@include display-flex(40rem);`
    second example
    ```
       @include display-flex(40rem){
         // everything here will be stored inside the @content
       }
    ```
- we can also nest the pseudo classes using the ampersand operator as `&:hover,&:active {....}`       
    





