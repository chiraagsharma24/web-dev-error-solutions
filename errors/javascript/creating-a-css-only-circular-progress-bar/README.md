# 🐞 Creating a CSS-Only Circular Progress Bar


This document details how to create a circular progress bar using only CSS.  No JavaScript required! This uses techniques applicable to both standard CSS and Tailwind CSS (though the example is in standard CSS for broader applicability).

**Description of the Styling:**

This technique leverages the `clip-path` property along with a rotated circle to create the visual effect of a progress bar.  A background circle represents the full circle, and a foreground circle, clipped using `clip-path`, represents the filled portion.  Rotating the foreground circle allows us to animate the progress.  The percentage is controlled by a CSS variable, making it easily adjustable.

**Full Code:**

```html
<!DOCTYPE html>
<html>
<head>
<title>CSS Circular Progress Bar</title>
<style>
.circular-progress {
  width: 150px;
  height: 150px;
  position: relative;
}

.circular-progress .circle {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  border: 5px solid #ccc; /* Background circle */
}

.circular-progress .circle-progress {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  border: 5px solid #4CAF50; /* Foreground circle */
  clip-path: polygon(50% 50%, 0% 0%); /* Initial clip */
  transform: rotate(calc(var(--progress) * 3.6deg)); /* Rotate for progress */
  transition: transform 0.5s ease; /* Smooth animation */
}

/* Example usage with different progress values */
.progress-50 .circle-progress {--progress: 50;}
.progress-75 .circle-progress {--progress: 75;}
.progress-100 .circle-progress {--progress: 100;}
</style>
</head>
<body>

<h1>CSS Circular Progress Bar</h1>

<div class="circular-progress progress-50">
  <div class="circle"></div>
  <div class="circle-progress"></div>
</div>

<div class="circular-progress progress-75">
  <div class="circle"></div>
  <div class="circle-progress"></div>
</div>

<div class="circular-progress progress-100">
  <div class="circle"></div>
  <div class="circle-progress"></div>
</div>


</body>
</html>
```

**Explanation:**

* **`--progress` variable:** This CSS custom property controls the percentage of the progress bar.  It's multiplied by `3.6deg` (360 degrees / 100) to calculate the rotation angle.
* **`clip-path: polygon(50% 50%, 0% 0%);`:** This initially clips the foreground circle to a triangle.  The rotation then reveals the filled portion.
* **`transform: rotate(calc(var(--progress) * 3.6deg));`:** This rotates the foreground circle based on the `--progress` variable.
* **`transition`:** This provides a smooth animation when the progress value changes.


**Links to Resources to Learn More:**

* **MDN Web Docs on `clip-path`:** [https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path)
* **CSS Tricks on Circular Progress Bars:** (Search for "CSS Circular Progress Bar" on CSS Tricks for various approaches)
* **Understanding CSS Variables (Custom Properties):** [https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

