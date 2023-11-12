# Week 6: HTML Element Types: Block vs. Inline

1. **Block-level elements:** These create a "block" of content on a page with an empty line before and after them. Block elements fill the width of their parent element and can contain other block elements, inline elements or text.

2. **Inline elements:** These create "inline" content, which is part of the containing block. Inline elements can contain other inline elements or text.

```html
<body>
    <p>The <em>cow</em> jumped over the <b>moon</b>.</p>
</body>
```

The `<p>` paragraph element is a block-level element. It fills its container (in this case, the `<body>` element) and has empty space added above and below it. Within this block, inline elements like simple text, `<em>` and `<b>` affect their content but do not create new blocks; they continue to flow inline within their container (the `<p>` element).

## Empty Elements

Some HTML elements do not need a closing tag because they have no content. These are referred to as "empty elements." Examples include `<br>` for line breaks, `<hr>` for horizontal lines, `<meta>` for metadata and others.

```html
<p>Knock, Knock<br>Who's there?</p>
```

## Grouping Elements

- `<header>`: Introductory material at the top of a document.
- `<nav>`: Content related to navigation, such as menus and links.
- `<main>`: The main content of the document.
- `<article>`: A self-contained composition like a blog post or article.
- `<section>`: A group of related elements representing one section of a whole.
- `<footer>`: End material like author information and copyright.

When there is not a suitable semantic container element:

- `<div>`: A generic block-level container.
- `<span>`: A generic inline container.

```html
<div>
    <p>This is an example of using a div element. It also includes this <span><em>span</em> element</span>.</p>
    <p>Later, div or span elements can be used to target content with JavaScript or apply CSS styles.</p>
</div>
```

## Tables

- `<table>`: The root element of an HTML table.
- `<caption>`: An optional title or caption for the table.
- `<thead>`: Row(s) at the top of the table (header row or rows).
- `<tbody>`: Rows that form the main body of the table (the table's content rows).
- `<tfoot>`: Row(s) at the bottom of the table (footer row or rows).

#### Define rows and columns using:

- `<tr>`: Represents a single row in a table.
- `<td>`: Represents a single cell (row/column intersection) containing table data.
- `<th>`: Represents a header, such as a title for a column.
- `rowspan` and `colspan` attributes to extend table elements beyond their usual bounds.

```html
<table>
    <caption>Order Information</caption>

    <thead>
        <tr>
            <th>Quantity</th>
            <th>Color</th>
            <th>Price (CAD)</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>1</td>
            <td>Red</td>
            <td>$5.60</td>
        </tr>
        <tr>
            <td>3</td>
            <td>Blue</td>
            <td>$3.00</td>
        </tr>
        <tr>
            <td>8</td>
            <td>Blue</td>
            <td>$1.50</td>
        </tr>
    </tbody>

    <tfoot>
        <tr>
            <th colspan="2">Total</th>
            <th>$26.60</th>
        </tr>
    </tfoot>
</table>
```

## Multimedia: `<img>`, `<audio>`, `<video>`

HTML5 supports the inclusion of images, audio and video in web content. Media sources and presentation are specified using different elements and attributes.

Examples:

- Including an image:
  ```html
  <!-- External image URL, full width of the browser window -->
  <img src="https://images.unsplash.com/photo-1502720433255-614171a1835e?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=344dfca9dc8cb137a4b1c2c711752bc5">
  ```

- Including audio:
  ```html
  <!-- No controls, music auto-plays in the background (only MP3 source provided) -->
  <audio src="https://ia800607.us.archive.org/15/items/music_for_programming/music_for_programming_1-datassette.mp3" autoplay></audio>
  ```

- Including video:
  ```html
  <!-- External video file (MP4 format) with controls -->
  <video src="http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" controls></video>
  ```

  ```html
  <!-- Local video file in various formats with controls -->
  <video width="320" height="240" controls>
      <source src="video.mp4" type="video/mp4">
      <source src="video.ogg" type="video/ogg">
      <source src="video.webm" type="video/webm">
      <p>Sorry, your browser doesn't support HTML5 video.</p>
  </video>
  ```

The `<audio>` and `<video>` elements should point to actual audio or video files and not URLs leading to HTML pages or other sources.

## Including Scripts

1. Inline Scripts: Embed JavaScript code directly within a `<script>` element in the HTML.

   Example:
   ```html
   <script>
       console.log('Hello World!');
   </script>
   ```

2. External Scripts Linked via URL: Include JavaScript code from external files by specifying a `src` attribute in the `<script>` element.

   Example:
   ```html
   <script src="script.js"></script>
   ```

## Validating HTML

Online HTML validators like [HTML5 Validator](https://html5.validator.nu/) or [W3C Markup Validation Service](https://validator.w3.org/) can be used to check HTML for errors or warnings.