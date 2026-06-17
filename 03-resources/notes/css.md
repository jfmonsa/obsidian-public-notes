---
mocs:
    - "[[public-notes/03-resources/frontend.md|Frontend]]"
tags:
    - dev/frontend
---

+ Cascading Style Sheets
+ Stylesheet language used to described the presentation of HTML and XML.
+ Each css module has is own versioning
---
+ 3 ways (native) of adding css to a document
# 1 - Basic Concepts
## Inheritance
+ Some css properties of an element are automatically applied to children elements
+ Generally the properties that affects text
## Specificity
+ is the algorithm that the browser uses to decide which property value is applied to an element
+ If multiple style blocks have different selectors that configure the same property with different values and target the same element, specificity decides the property value that gets applied to the element.
---
Specificity is calculated using a four-part value (a, b, c, d):

- **a**: Inline styles (e.g., `style="..."`) have the highest specificity.
- **b**: ID selectors (e.g., `#header`) are highly specific.
- **c**: Class selectors (e.g., `.btn`), attribute selectors (e.g., `[type="text"]`), and pseudo-classes (e.g., `:hover`).
- **d**: Element selectors (e.g., `div`, `p`) and pseudo-elements (e.g., `::before`, `::after`).

```css
body .container #header .highlighted {
  color: purple;
}

/* specificity (0,1,2,1)*/
```
## Cascading
+ the way that styles are applied to HTML elements, particularly how conflicts between different styles are resolved.
---
1. **source order**: two rules with equal specificity, the las overrides the first
2. **specificity**
3. important!
4. inheritance
---
+ also there's the concept of cascade layers (author defined styles vs user-agent)
## Mix Concepts
+ Vendor Prefixes
+ Shorthand Properties
+ Normalizer: Normalize CSS
```css
* {
box-sizing: border-box;
padding: 0;
margin: 0; }
```
+ Browser Default Styles
+ at-rules `@`
+ CSS functions
+ variables
**Sintax**
+ Declaration block
+ Declaration
+ rule: selector + declaration block
---
+ Display: none vs Visibility: Hidden
# 2 - Selectors
+ element / tagname / type selector
+ classname (`.`)
+ id (`#`)
+ based on state (pseudo-classes): `button:hover`
+ pseudo-elements. e.g `::first-line, ::before, ::after, ::first-letter`
+ combinators: `+` (next sibling),`>` (children),` ` (descendant), `~` subsequent sibling
+ universal selector `*`
+ attribute selector
---
+ nesting: `&` (refers to parent selector)
# 3 - Box Model
## Block and inline elements
+ **Block**: take up the full width available (if width no specified)
+ **inline**: they flow within the text. Can have margins and padding, but these only affect the left and right sides without disrupting the flow of the text.
## Parts (properties)
1. content
2. padding
3. border
4. marging
![[Pasted image 20250125102429.png]]
## Inner and outer display types
### Outer
The outer display type determines how an element behaves in the layout flow of the document. Common values include:
+ values of `display`: block, inline, inline-block
### Inner
The inner display type determines how the children of the element are laid out. Common values include:
+ values: `flex`, `grid`
## Standard CSS box model vs border-box
**Standard box model**
+ `width` and `height` define the content box, any padding and borders are added to those dimension
**box-sizing: border-box (Preferred)** 
## Margin collapsing
+ vertical margins of adjacent block-level elements collapse into a single margin, rather than adding together.
+ - resulting margin between them will be equal to the larger of the two margins.
# 4 - Values and units
+ value types: e.g.: `<color>` (angle brackets
## `<length>`
+ absolute units: `pc`, `px`
+ relative unit length: `em`, (my parents element font-size) `rem`,`vw`,`vh`, `%`
## `<color>
+ rgb(), rgba(), hex,
# 5 - Sizing
+ set `width`, `height`, `min-height`, `max-height`
# 6 - Background & Borders
+ `background-color`
+ `background-image`, `background-repeat`, `background-size: cover | contain`, `background-position`
+ `gradients`
---
+ `border`
+ `border-radious`
# 7 - Overflowing Content
+ `overflow: hidden | scroll | auto`, `overflow-y`, `overflow-x`
# 8 - images, media
+ `max-width: 100%;`
+ `object-fit: cover`
+ `object-fit: contain;`
# 9 - Fonts
+ `font-weight`, `font-style`, `text-transform: uppercsase`, `text-decoration`, `text-shadow`
+ `text-align: center | justify | right`
+ `line-height: value`: fontsize gets multiplied by a value
+ `letter-spacing`,  `word-spacing`, `text-indent`
+ set relative sizes for fonts
# 8 - Layouts
+ Flex
+ grid
+ float (only use it for image + text)
+ positioning:
	+ **static**: default value for every element
	+ **relative**: positioned relative to normal position
	+ **absolute**: positioned relative to nearest positioned ancestor
	+ **fixed**: positioned relative to the viewport
	+ **sticky**: toggles between relative and fixed
	+ top, left, right, bottom
	+ **stacking contexts and z-index**: determined the order elements are displayed in z-axis
# Responsive
+ images: `max-width: 100%`
+ adaptable font
+ media queries
+ grid, flex
# Transform
+ `transalate()`
+ `rotate()`
+ `scale()`
# Frameworks, libraries
+ Taildwind
+ UnoCSS
---
+ DaisyUI: UI library use taildwind
+ vuetify components
+ Shadcn: React
+ MUI: React
---
# Architecture
+ with `@layer` layers: framework > globals > components > utilities.
	+ This means later layers will override
+ BEM architecture

# HTML
+ Hypertext Markup Language
---
## Notes
+ `<dialog>`: for modals