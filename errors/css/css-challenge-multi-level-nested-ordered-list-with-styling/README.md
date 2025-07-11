# 🐞 CSS Challenge:  Multi-level Nested Ordered List with Styling


This challenge focuses on styling a multi-level nested ordered list using CSS. We'll create a visually appealing and easily readable nested list with distinct styling for each level.  We'll use standard CSS for this example, but the principles could be easily adapted to a CSS framework like Tailwind CSS.

**Description of the Styling:**

The goal is to style a nested ordered list to clearly differentiate between the different levels. We will achieve this by:

* Indenting subsequent list levels.
* Using different list-style-types (e.g., decimal, lower-alpha) for each level.
* Applying different font sizes and weights for better readability.
* Adding background colors to visually separate list items.


**Full Code:**

```html
<!DOCTYPE html>
<html>
<head>
<title>Nested Ordered List</title>
<style>
ol {
  list-style-type: decimal;
  margin-left: 20px;
  padding-left: 0; /* Remove default padding */
  font-size: 16px;
}

ol ol {
  list-style-type: lower-alpha;
  margin-left: 40px;
  font-size: 14px;
}

ol ol ol {
  list-style-type: disc;
  margin-left: 60px;
  font-size: 12px;
}

li {
  padding: 5px 0; /* Add some spacing */
}

ol li {
  background-color: #f2f2f2;
}

ol ol li {
  background-color: #e0e0e0;
}

ol ol ol li {
  background-color: #d0d0d0;
}

</style>
</head>
<body>

<h1>Nested List Example</h1>

<ol>
  <li>Item 1</li>
  <li>Item 2
    <ol>
      <li>Sub-item 2.1</li>
      <li>Sub-item 2.2
        <ol>
          <li>Sub-sub-item 2.2.1</li>
          <li>Sub-sub-item 2.2.2</li>
        </ol>
      </li>
      <li>Sub-item 2.3</li>
    </ol>
  </li>
  <li>Item 3</li>
</ol>

</body>
</html>
```

**Explanation:**

* The main `ol` style sets the base style for the top-level list.
* Nested `ol` selectors (`ol ol`, `ol ol ol`) target subsequent levels and apply specific styles like indentation, list-style-type, and font size.
* The `li` selectors apply padding and background colors to improve visual clarity and separation between list items.  Each level gets a slightly different background color to visually highlight the nesting.


**Links to Resources to Learn More:**

* **MDN Web Docs - CSS Lists:** [https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type)  This provides comprehensive information on styling lists in CSS.
* **CSS Tricks - List Styles:**  Search "CSS Tricks list styles" on Google for numerous articles and tutorials on advanced list styling techniques.  (Note:  Specific URLs to articles are dynamic and change frequently).


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

