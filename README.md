# Interactive 3D Card

This project is a simple web page showcasing an interactive 3D card effect using HTML, CSS, and jQuery. The card responds to mouse movement, creating a subtle 3D parallax and tilt effect.



## -Features

* **3D Tilt Effect:** The main card (`.card`) tilts on the X and Y axes as the user moves the mouse over the container, giving it a depth-of-field effect using CSS `transform` and `perspective`.
* **Exaggerated Parallax on Hover:** When the mouse hovers over the container, the card and its internal elements (`.teks img`, `.purchase`) receive an additional `translateZ` transformation, making them appear to pop out.
* **Animated Background:** A simple yet engaging background animation is implemented using an unordered list (`.box-area li`) with CSS animations to create floating, fading boxes.
* **Responsive Design:** The layout uses percentages and `clamp()` for some font sizes, making it reasonably adaptable to different screen sizes.

## -Technologies Used

* **HTML5**
* **CSS3** (with embedded `<style>` block)
* **JavaScript** (using **jQuery** library)

## -Getting Started

To run this project, you only need to save the provided code as an HTML file (e.g., `index.html`) and ensure you have the necessary external resources.

### Prerequisites

1.  **jQuery:** The project uses jQuery, which is linked via a CDN:
    ```html
    <script src="[https://code.jquery.com/jquery-3.6.0.min.js](https://code.jquery.com/jquery-3.6.0.min.js)"></script>
    ```
2.  **AOS (Animate On Scroll):** Although `AOS.init()` is called, no actual "Animate On Scroll" elements are used in the provided HTML structure. It is linked via a CDN:
    ```html
    <script src="[https://unpkg.com/aos@next/dist/aos.js](https://unpkg.com/aos@next/dist/aos.js)"></script>
    ```
3.  **Image Assets:** The code references the following local images, which you would need to replace or include in an `img/` folder:
    * `img/ai-kite.jpg` (for the card's background)
    * `img/mark_black.png`
    * `img/kite-tz.png`

### Installation

1.  Save the code as `index.html`.
2.  Create an `img` folder and place your image assets inside it, or update the image paths in the HTML and CSS.
3.  Open `index.html` in your web browser.

## -Code Overview

### HTML Structure (`<body>`)

The main elements are:

* `<body class="animation-area">`: Contains the background animation elements.
* `<ul class="box-area">`: Creates the floating boxes for the background animation.
* `<div class="container">`: The area where the mouse movement is tracked.
* `<div class="card">`: The main 3D-transformable element.
* `<div class="teks">`: Containers for the images inside the card.
* The second image has the class `zoom-in-zoom-out` for a pulsating animation.

### CSS (`<style>`)

* **3D Setup:** The `container` and `card` use `perspective` and `transform-style: preserve-3d` to enable the 3D effects.
* **Mouse Interaction Classes:**
    * `.card.has-transform`
    * `.teks img.has-transform`
    * `.purchase.has-transform`
    These classes are added/removed by JavaScript on hover to apply the exaggerated `translateZ` effect.
* **Animations:**
    * `@keyframes zoom-in-zoom-out`: Makes the central image pulsate.
    * `@keyframes animate`: Moves the background boxes upward and fades them out.

### JavaScript (jQuery)

The script handles the two main interactive behaviors:

1.  **Mousemove Tilt:**
    ```javascript
    $container.on("mousemove", function (e) {
      let xAxis = (window.innerWidth / 2 - e.clientX) / 25; // Calculate tilt based on mouse position
      let yAxis = (window.innerHeight / 2 - e.clientY) / 25;
      $card.css("transform", `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`);
    });
    ```
2.  **Hover Pop-out Effect:**
    ```javascript
    $container.hover(function () {
      // Toggle 'has-transform' classes to apply pop-out effect
      $card.toggleClass("has-transform");
      $teks.toggleClass("has-transform");
      $purchase.toggleClass("has-transform");
    });
    ```
    And on mouse leave, the tilt is reset:
    ```javascript
    $container.on("mouseleave", function () {
      $card.css("transform", `rotateY(0deg) rotateX(0deg)`);
    });
    ```

## 📄 License

This project is open-source. Feel free to use and modify it.
