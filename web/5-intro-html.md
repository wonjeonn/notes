# Week 5: Introduction to HTML

## HTML - HyperText Markup Language

**HTML (HyperText Markup Language)** is the standard markup language for creating web pages, allowing the structure and formatting of content for the web.

- **Content:** Text or information included in a web page can be written as-is.

- **Tag:** Special text enclosed in `<` and `>` characters, defining elements in HTML. Examples include the paragraph tag `<p>` or the image tag `<img>`.

- **Element:** A complete structure defined by an opening tag, content and a closing tag. For instance, an `<h1>` element includes the opening `<h1>` tag, content ("Chapter 1") and closing `</h1>` tag.

- **Attribute:** Optional characteristics of an element, defined using attributes such as `name="value." For example, `<p id="error-message" hidden>` has two attributes: `id` with the value "error-message" and `hidden."

- **Entity:** Special text enclosed between `&` and `;` characters, used to represent characters with special meanings in HTML. For example, `&lt;` for `<`, `&nbsp;` for a single space and `&amp;` for `&."

## HTML5 Document Structure

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>My Web Page</title>
    </head>
    <body>
        <!-- This is a comment -->
        <h1>Hello World!</h1>
    </body>
</html>
```

- `<!doctype html>` specifies that the document is in HTML5 format.

- `<html>` is the root element containing all other elements.

- `<head>` provides machine-readable metadata about the document, including the character set.

- `<meta>` defines the character set (e.g., utf-8) used in the document.

- `<title>` sets the document's title, which appears in the browser's title bar.

- `<body>` contains the document's content.

- `<!-- ... -->` is a comment, used to add notes or explanations in the HTML code.

- `<h1>` is a heading element. HTML headings from `<h1>` (highest importance) to `<h6>` (lowest importance).

## Common HTML Elements

- **Metadata Elements:**
  - `<link>`: Links to external resources like CSS stylesheets.
  - `<meta>`: Defines metadata about the document.
  - `<title>`: Specifies the document's title.

- **Major Document Sections:**
  - `<html>`: The root element containing all other elements.
  - `<head>`: Contains machine-readable metadata.
  - `<body>`: Houses the document's content.

- **Content Sections:**
  - `<header>`: Contains introductory material at the top of the document.
  - `<nav>`: Includes content related to navigation (e.g., menus, links).
  - `<main>`: Represents the main content of the document.
  - `<h1>`, `<h2>`, ... `<h6>`: Define headings of different levels.
  - `<footer>`: Contains end materials like author information and copyright.

- **Text Content:**
  - `<div>`: A generic container for attaching CSS styles to a specific content area.
  - `<ol>`: Represents an ordered list (e.g., 1, 2, 3) of list items.
  - `<ul>`: Indicates an unordered list (bulleted) of list items.
  - `<li>`: Represents a list item in an ordered or unordered list.
  - `<p>`: Defines a paragraph.
  - `<blockquote>`: Represents an extended quotation.

- **Inline Text Elements:**
  - `<a>`: Creates hyperlinks, allowing users to navigate to other documents.
  - `<code>`: Formats text as computer code.
  - `<em>`: Adds emphasis to text (often displayed in italics).
  - `<span>`: A generic container used to define CSS styles.

- **Multimedia Elements:**
  - `<img>`: Embeds images in a document.
  - `<audio>`: Embeds sound in a document.
  - `<video>`: Embeds video in a document.
  - `<canvas>`: A graphical area used for drawing with JavaScript (2D or 3D).

- **Scripting Elements:**
  - `<script>`: Embeds executable code in a document, typically JavaScript.