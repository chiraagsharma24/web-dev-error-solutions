# 🐞 Creating a CSS-only Accordion


This document details the creation of an accordion using only CSS.  No JavaScript is required. This example uses standard CSS, but the principles can be easily adapted to frameworks like Tailwind CSS.

**Description of the Styling:**

This accordion utilizes CSS's `:target` pseudo-class to control the visibility of the content panels.  Each accordion item has a heading that acts as a link to a specific section. Clicking the heading changes the URL's hash, revealing or hiding the corresponding content.  The styling focuses on creating a clean, visually appealing accordion with smooth transitions.

**Full Code:**

```html
<!DOCTYPE html>
<html>
<head>
<title>CSS Only Accordion</title>
<style>
body {
  font-family: sans-serif;
}

.accordion {
  width: 300px;
  border: 1px solid #ccc;
}

.accordion-item {
  border-bottom: 1px solid #ccc;
}

.accordion-item h2 {
  background-color: #f0f0f0;
  padding: 10px;
  cursor: pointer;
  transition: background-color 0.3s ease; /* Smooth transition for hover effect */
}

.accordion-item h2:hover {
  background-color: #ddd;
}

.accordion-content {
  padding: 10px;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease; /* Smooth transition for content reveal */
}

.accordion-item:target > .accordion-content {
  max-height: 200px; /* Adjust as needed */
}
</style>
</head>
<body>

<div class="accordion">
  <div class="accordion-item">
    <h2 id="section1">Section 1</h2>
    <div class="accordion-content">
      <p>Content for Section 1.</p>
    </div>
  </div>
  <div class="accordion-item">
    <h2 id="section2">Section 2</h2>
    <div class="accordion-content">
      <p>Content for Section 2.</p>
    </div>
  </div>
  <div class="accordion-item">
    <h2 id="section3">Section 3</h2>
    <div class="accordion-content">
      <p>Content for Section 3.</p>
    </div>
  </div>
</div>

</body>
</html>
```

**Explanation:**

* **`max-height: 0; overflow: hidden;`**:  Initially hides the content.
* **`transition: max-height 0.3s ease;`**: Creates a smooth transition when the `max-height` changes.
* **`:target > .accordion-content`**: This is the key selector. It targets the `.accordion-content` element only when its parent (`accordion-item`) is the target of a URL hash.  For example, clicking on `<h2 id="section1">` changes the URL to `#section1`, making the `.accordion-content` within that `.accordion-item` element the target and showing its content.
* **`max-height: 200px;`**:  Sets the maximum height when expanded.  Adjust this value to control the visible content height.


**Links to Resources to Learn More:**

* **MDN Web Docs on CSS Selectors:** [https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) (Specifically, learn about the `:target` pseudo-class)
* **CSS Transitions Tutorial:**  [Search for "CSS Transitions tutorial" on your preferred search engine]


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

