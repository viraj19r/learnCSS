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

