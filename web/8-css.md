# Week 8: Cascading Style Sheets (CSS)

## CSS Basics

**Separation of Structure and Style:**
- HTML focuses on structure and content.
- CSS is used for styling and layout.

**CSS Syntax:**
- CSS rules consist of selectors and declarations.
- Selectors target HTML elements and declarations define the style.

```css
selector {
    property: value;
}
```

**CSS Selectors:**
- **Tag/Type** Selectors: Select elements based on their HTML tag.
- **Class** Selectors: Select elements with a specific class attribute.
- **ID** Selectors: Select a unique element with a specific ID attribute.
- Contextual Selectors: Select elements based on their nesting in the HTML structure.
- Grouping Selectors: Group multiple selectors to apply the same styles.

## Applying CSS

**Inline, Internal and External CSS:**
- Inline styles are applied directly to HTML elements using the `style` attribute.
- Internal styles are defined within `<style>` tags in the HTML `<head>` or `<body>`.
- External styles are stored in separate CSS files linked using `<link>` tags.

**Styling Links:**
- CSS pseudo-classes (`:link`, `:visited`, `:hover`, `:active`) are used to style links based on their state.

## CSS Properties and Values

**Font Properties:**
- `font-family`: Specifies the font for an element.
- `font-size`: Sets the size of the font.
- `font-weight`, `font-style`: Controls the weight and style of the font.

**Background Properties:**
- `background-color`: Sets the background color of an element.
- `background-image`: Specifies a background image.
- `background-repeat`: Defines how the background image should repeat.

**Text Properties:**
- `color`: Sets the text color.
- `text-align`, `text-decoration`, `text-transform`: Control text alignment, decoration and transformation.

**Other CSS Effects:**
- `text-shadow`: Adds a shadow effect to text.
- `text-overflow`: Defines how text behaves when it overflows its container.
- Various effects can be achieved using CSS, enhancing the visual appeal of elements.

## Manipulating CSS with JavaScript

**Using `style` and `classList` Properties:**
- JavaScript can manipulate CSS properties of elements using the `style` property.
- The `classList` property provides methods like `add()`, `remove()` and `toggle()` to modify CSS classes dynamically.

**Changing CSS Classes Dynamically:**
- JavaScript can add, remove or replace CSS classes based on user interactions or application logic.

## CSS Box Model

The CSS Box Model describes how elements are rendered on a web page.

- **Content:** This is the actual content of the element, such as text, images or other media.

- **Padding:** Padding is the space between the content and the element's border. It can be adjusted using properties like `padding-top`, `padding-right`, `padding-bottom` and `padding-left`.

- **Border:** The border surrounds the element's padding and content. It can be controlled its style, width and color using properties like `border-style`, `border-width` and `border-color`.

- **Margin:** Margin is the space between the border of an element and other neighboring elements. It can be adjusted using properties like `margin-top`, `margin-right`, `margin-bottom` and `margin-left`.

## CSS Display Property

The `display` property in CSS controls how an element is rendered in the DOM.

- `none`: The element and its children are not displayed on the page.
- `block`: Elements are displayed as block-level elements, stacking vertically with each other.
- `inline`: Elements are displayed inline, stacking horizontally within their parent element.
- `inline-block`: Elements are displayed as inline, but can have block-level properties.
- `flex`: Used for creating flexible box layouts (Flexbox).
- `grid`: Used for creating grid-based layouts (CSS Grid).

## CSS Position Property

The `position` property in CSS allows controlling the positioning of an element within its container, often used in combination with the `top`, `right`, `bottom` and `left` properties to precisely position elements on a webpage.

- `static` (default): The element is positioned in the normal flow of the document.
- `relative`: The element is positioned relative to its normal position and it can be shifted using the `top`, `right`, `bottom` and `left` properties.
- `absolute`: The element is removed from the normal document flow and is positioned relative to its closest positioned ancestor. It won't affect the layout of other elements.
- `fixed`: The element is positioned relative to the viewport, so it stays in the same position even when scrolling.
- `sticky`: The element is initially in the normal flow but becomes fixed when it reaches a specified scroll position.

## CSS z-index Property

The `z-index` property is used to control the stacking order of elements when they overlap in the z-axis (vertical stacking order). Elements with higher `z-index` values are rendered on top of elements with lower values. The default `z-index` value is 0.

This property is commonly used when working with positioned elements, such as pop-up windows, dropdown menus or modal dialogs, to control which elements appear in front of others.

## CSS Overflow Property

The `overflow` property in CSS controls how content that overflows an element is displayed. `overflow-x` and `overflow-y` properties can be used to control overflow behavior horizontally and vertically, respectively.

- `visible`: Content is not clipped and overflow is visible outside the element's box.
- `hidden`: Content is clipped and overflow is not visible.
- `scroll`: Scrollbars are always displayed, allowing users to scroll to see the overflowing content.
- `auto`: Scrollbars are displayed only when necessary, based on the content size and the element's dimensions.
