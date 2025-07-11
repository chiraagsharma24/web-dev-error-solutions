# 🐞 CSS Challenge:  Multi-level Nested List with Custom Styling


This challenge focuses on styling a multi-level nested list using CSS. We'll create a visually appealing and easily navigable list with distinct styling for each level. We will use standard CSS for this example.


## Description of the Styling

The goal is to create a nested list where:

* The top-level list items (`<li>`) have a larger font size and are bolded.
* Each subsequent level is indented further and has a smaller font size.
*  List markers are replaced with custom icons (using background images for simplicity).
*  A subtle background color alternates between list levels to enhance readability.

## Full Code

```html
<!DOCTYPE html>
<html>
<head>
<title>Nested List Styling</title>
<style>
ul {
  list-style: none; /* Remove default bullet points */
  padding: 0;
  margin-left: 20px; /* Initial indent */
}

li {
  margin-bottom: 10px;
}

li::before {
  content: ""; /* Add content for custom icons */
  display: inline-block;
  width: 20px;
  height: 20px;
  margin-right: 10px;
  background-repeat: no-repeat;
  background-size: contain;
}

ul.level-1 > li {
  font-size: 18px;
  font-weight: bold;
  background-color: #f9f9f9;
  padding: 10px;
  margin-left: 0; /* Remove the default indentation from first level */
  
}
ul.level-1 > li::before {
  background-image: url('folder-icon.png'); /* Replace with your icon */
}

ul.level-2 > li {
  font-size: 16px;
  background-color: #f2f2f2;
  padding: 5px;
}
ul.level-2 > li::before {
  background-image: url('file-icon.png'); /* Replace with your icon */
}

ul.level-3 > li {
  font-size: 14px;
  background-color: #f9f9f9;
  padding: 5px;
}
ul.level-3 > li::before {
  background-image: url('document-icon.png'); /* Replace with your icon */
}

/* Add more styles for deeper levels as needed */
</style>
</head>
<body>

<h1>My Documents</h1>

<ul class="level-1">
  <li>Project Alpha
    <ul class="level-2">
      <li>Report.pdf</li>
      <li>Presentation.pptx</li>
    </ul>
  </li>
  <li>Project Beta
    <ul class="level-2">
      <li>Design Mockups
        <ul class="level-3">
          <li>Homepage.jpg</li>
          <li>AboutUs.png</li>
        </ul>
      </li>
      <li>Code.zip</li>
    </ul>
  </li>
</ul>

</body>
</html>

```

Remember to replace  `folder-icon.png`, `file-icon.png`, and `document-icon.png` with actual paths to your icon images.


## Explanation

The CSS code uses a combination of list-style removal, pseudo-elements (`::before`), and class-based styling to achieve the desired visual hierarchy.  Each level of the nested list gets its own class (`.level-1`, `.level-2`, `.level-3`) allowing for specific font sizes, background colors, and icon assignments. The `::before` pseudo-element adds the custom icon before each list item.  The `background-image` property sets the icon. You can adjust the font sizes, colors, indentation, and icon sizes to your preference.


## Resources to Learn More

* **MDN Web Docs CSS Reference:** [https://developer.mozilla.org/en-US/docs/Web/CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)  (Excellent resource for all things CSS)
* **CSS Tricks:** [https://css-tricks.com/](https://css-tricks.com/) (A website with tutorials and articles on CSS techniques)


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

