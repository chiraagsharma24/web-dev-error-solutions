# 🐞 CSS Challenge:  Animated Circular Progress Bar with Tailwind CSS


This challenge involves creating an animated circular progress bar using Tailwind CSS.  The progress bar will visually represent a percentage value, updating smoothly as the percentage changes. We'll use CSS variables and animations to achieve a clean and efficient solution.

**Description of the Styling:**

The progress bar will be a circle with a background color.  A semi-circle overlay will represent the progress, filling in from the right. The percentage value will be displayed in the center of the circle.  The animation will involve the semi-circle smoothly expanding or contracting to reflect the percentage change.  We'll leverage Tailwind's utility classes for easy styling and responsive design.


**Full Code:**

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Circular Progress Bar</title>
<script src="https://cdn.tailwindcss.com"></script>
<style>
  .progress-ring {
    --progress: 0; /*initial value*/
    width: 150px;
    height: 150px;
    border-radius: 50%;
    background-color: #e0e0e0;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    animation: animateProgress 2s forwards; /*animation to start*/
  }

  .progress-ring::before {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background-color: #4299E1;
    clip: rect(0, 50%, 100%, 0); /*half circle*/
    transform: rotate(calc(var(--progress) * 3.6deg));
    transform-origin: 50% 100%; /*rotation point*/
    animation: animateProgress 2s forwards;
  }

  .progress-ring .percentage {
    z-index: 1; /*make sure text is visible above the semi-circle*/
    font-size: 1.2rem;
    color: #fff;
  }


  @keyframes animateProgress{
    from {--progress: 0}
    to {--progress: var(--percentage)}
  }
</style>
</head>
<body class="bg-gray-100 flex justify-center items-center h-screen">
  <div class="progress-ring" style="--percentage: 75">  <!--Change this value to adjust initial percentage-->
    <span class="percentage">75%</span>
  </div>


</body>
</html>
```

**Explanation:**

* **Tailwind Classes:** We use `bg-gray-100`, `flex`, `justify-center`, `items-center`, and `h-screen` for basic layout and styling.
* **CSS Variables:** `--progress` dynamically controls the animation, representing the percentage converted into degrees. `--percentage` is a custom property that sets the target percentage.

* **Pseudo-element `::before`:** This creates the semi-circle that visually represents the progress. `clip` creates the semi-circle shape. `transform: rotate()`  rotates it based on the `--progress` value.


* **`animateProgress` Keyframes:** This animation smoothly updates the `--progress` variable, driving the progress bar animation.


* **Javascript (Optional):**  You can easily integrate JavaScript to dynamically change the `--percentage` CSS variable, allowing for real-time progress updates.


**Links to Resources to Learn More:**

* **Tailwind CSS Documentation:** [https://tailwindcss.com/docs](https://tailwindcss.com/docs)
* **CSS Variables (Custom Properties):** [https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
* **CSS Animations:** [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Animations/Using_CSS_animations)


Copyrights (c) OpenRockets Open-source Network. Free to use, copy, share, edit or publish.

