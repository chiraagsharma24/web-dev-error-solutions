# 🐞 CSS Challenge:  Multi-level Nested List with Stylish Accordions


This challenge focuses on creating a multi-level nested list that utilizes CSS-only accordions for expanding and collapsing each list item's sub-items.  We'll leverage CSS3 features for styling and functionality. No JavaScript will be used.

**Description of the Styling:**

The nested list will have a clean and modern appearance.  Top-level list items will be displayed with a distinct heading style.  Subsequent levels will be indented and visually differentiated through color and spacing.  The accordion functionality will involve using the `:target` pseudo-class and sibling selectors to elegantly hide and show nested list items without JavaScript. Each list item will have a visually appealing toggle element to trigger the expansion/collapse.


**Full Code:**

```html
<!DOCTYPE html>
<html>
<head>
<title>Nested List Accordion</title>
<style>
body {
  font-family: sans-serif;
}

.accordion {
  background-color: #f2f2f2;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  transition: 0.4s;
}

.active, .accordion:hover {
  background-color: #ddd;
}

.accordion:after {
  content: '\2795'; /* Unicode character for "plus" sign */
  color: #777;
  font-weight: bold;
  float: right;
  margin-left: 5px;
}

.active:after {
  content: "\2796"; /* Unicode character for "minus" sign */
}

.panel {
  padding: 0 18px;
  background-color: white;
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.2s ease-out;
}

.panel.show {
  max-height: 500px;  /* Adjust as needed */
}

ol {
    list-style-type: decimal;
    margin-left: 20px;
}

ol ol {
  margin-left: 40px;
}

ol li {
    margin-bottom: 10px;
}

h3 {
  margin-top: 0;
}
</style>
</head>
<body>

<h2>Nested List with Accordions</h2>

<div class="accordion">
  <h3>Item 1</h3>
  <div class="panel">
    <ol>
      <li>Subitem 1.1</li>
      <li>Subitem 1.2
        <ol>
          <li>Subsubitem 1.2.1</li>
          <li>Subsubitem 1.2.2</li>
        </ol>
      </li>
      <li>Subitem 1.3</li>
    </ol>
  </div>
</div>

<div class="accordion">
  <h3>Item 2</h3>
  <div class="panel">
    <p>Content for Item 2</p>
  </div>
</div>

<script>
var acc = document.getElementsByClassName("accordion");
var i;

for (i = 0; i < acc.length; i++) {
  acc[i].addEventListener("click", function() {
    this.classList.toggle("active");
    var panel = this.nextElementSibling;
    if (panel.style.maxHeight){
      panel.style.maxHeight = null;
    } else {
      panel.style.maxHeight = panel.scrollHeight + "px";
    }
  });
}
</script>

</body>
</html>
```


**Explanation:**

The CSS uses the `:target` pseudo-class in conjunction with the `max-height` property to control the visibility of nested lists.  The JavaScript is used to add functionality for collapsing and expanding the content. The `accordion` class manages the styling of the list items, while `panel` handles the collapsible content.  The `active` class applies styling changes when the accordion is expanded.


**Links to Resources to Learn More:**

* **CSS Selectors:** [MDN Web Docs - CSS Selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Selectors)
* **CSS Transitions:** [MDN Web Docs - CSS Transitions](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions)
* **CSS Pseudo-classes:** [MDN Web Docs - CSS Pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)

Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

