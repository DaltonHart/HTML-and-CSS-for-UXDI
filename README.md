# HTML and CSS for UXDI

## The Browser
Let's understand the browser a bit more.

### The languages that make up the web.
- HTML
    - The "structure" of a web site.
- CSS
    - The "design" portion of a web site.
- Javascript
    - The "functionality" of a web site.

### The Pixel Pipeline
![Pixel Pipeline](https://developers.google.com/web/fundamentals/performance/rendering/images/intro/frame-full.jpg)

- **JavaScript**. Typically JavaScript is used to handle work that will result in visual changes, whether it’s jQuery’s animate function, sorting a data set, or adding DOM elements to the page. It doesn’t have to be JavaScript that triggers a visual change, though: CSS Animations, Transitions, and the Web Animations API are also commonly used.
- **Style calculations**. This is the process of figuring out which CSS rules apply to which elements based on matching selectors, for example, `.headline` or `.nav > .nav__item.` From there, once rules are known, they are applied and the final styles for each element are calculated.
- **Layout**. Once the browser knows which rules apply to an element it can begin to calculate how much space it takes up and where it is on screen. The web’s layout model means that one element can affect others, for example the width of the `<body>` element typically affects its children’s widths and so on all the way up and down the tree, so the process can be quite involved for the browser.
- **Paint**. Painting is the process of filling in pixels. It involves drawing out text, colors, images, borders, and shadows, essentially every visual part of the elements. The drawing is typically done onto multiple surfaces, often called layers.
- **Compositing**. Since the parts of the page were drawn into potentially multiple layers they need to be drawn to the screen in the correct order so that the page renders correctly. This is especially important for elements that overlap another, since a mistake could result in one element appearing over the top of another incorrectly.

## HTML
*Hyper Text Markup Language*
There are two main areas to an HTML Document. The **Head** and the **Body**.

The **Head** holds the meta data of the site. This includes links to other files and important information including how to detect the screen size.

Let's look at an example of the head tag for our coding exercise. 

``` html=
<head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.11.2/css/all.css">
</head>
```

The **Body** holds the rendered content of the website. This is what the user will see and interact with. This in most cases have an internal split of a Header, Main, Footer and maybe an aside. Other wise known as the holy grail layout. 

Let's look at an example of the head tag for our coding exercise.

```html=
<body>
    <div id="button" class="share__button">
      <span class="share__button__cover">
        <i class="fas fa-share-alt"></i>
        Share!
      </span>
  </div>
</body>
```

*Take notice of the class and id properties.* 

**Class** is used for defining and trgeting a collection of elements.
For example: in a gallery all images would share a class to give them all the same styles.

**Id** is used for unique defining and selection. Only one element can have a unique id. 
For example: an id would be given to a button that is suppose to execute a specific action unique to itself.

## CSS
*Cascading Style Sheets*

Let's look at the syntax for CSS.

```css=
selector {
    property: value;
    property: value;
    property: value;
}
```

The **Selector** can either be an html element, a class, or an id. We use the selctor do do exactly what you think. Target something and apply styles. 

For Example:
```css=
body {
  margin:0;
  padding:0;
  font-family: "montserrat", sans-serif;
  background: #f1f1f1;
}
.share__button {
  width: 280px;
  height: 80px;
}
```

## Activity 
![coding](https://media.giphy.com/media/PiQejEf31116URju4V/giphy.gif)

Let's build an [interactive share button](https://codepen.io/DaltonH/pen/NWPaOYN?editors=1000)! 
This is what we shall be building.


Let's head on over to [Codepen](https://codepen.io/). This is an online frontend developer community that will allow us to develop code without having to install anything on our machine.

### HTML
Let's get down the base of our HTML and talk about the elements.
In our head we are linking to an external library that will give us access to cool icons! 

```html=
<head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.11.2/css/all.css">
</head>

<body>
    <div class="share__button">
      <span class="share__button__cover">
        <i class="fas fa-share-alt"></i>
        Share!
      </span>
    <!--   ICONS Go Here     -->
  </div>
</body>
```

Let's add in our Font awesome links and icons now.

```html=
<!--   facebook     -->
      <a class="share__icon--facebook" href="#">
        <i class="fab fa-facebook-f" ></i>
      </a>
<!--    twitter    -->
      <a class="share__icon--twitter" href="#">
        <i class="fab fa-twitter"></i>
      </a>
<!--    instagram    -->
      <a class="share__icon--instagram" href="#">
        <i class="fab fa-instagram"></i>
      </a>
<!--    linkedin    -->
      <a  class="share__icon--linkedin" href="#">
        <i class="fab fa-linkedin-in"></i>
      </a>
```

And that's it! Take note of the way it looks so far. We only have our structure. But, all browsers have inate styles. Time to introduce our styles! 

### CSS

First we will target and apply styles to the body element. 

```css=
body {
  margin:0;
  padding:0;
  font-family: "montserrat", sans-serif;
  background: #f1f1f1;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
```

*What happened to our elements?*

Next is to get our button into postiion and shapped out.

```css=
.share__button {
  width: 280px;
  height: 80px;
  background: #dfe6e9;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  cursor: pointer;
  transition: .3s linear;
  overflow: hidden;
}
```
*Note how the elements have adjusted with each property. We have now centered all the content inside the button.*

Let's add that grow hover effect! For this we will be using a psuedo selector. 

```css=
.share__button:hover{
  transform: scale(1.1);
}
```

*As we can see now, when we hover over the button we get a small interaction that grows the button.*

Next step is pull out that cover and over lay it on top.
```css=
.share__button__cover {
  position: absolute;
  font-size: 1.6em;
  width: 100%;
  height: 100%;
  background: #2d3436;
  color: #f1f1f1;
  text-align: center;
  line-height: 80px;
  z-index: 2;
  transition: .4s linear;
  border-radius: 20px;
}
```
Looking good! But we need to add a hover effect to the cover to transition it.

```css=
.share__button:hover .share__button__cover {
  transform: translateX(-100%);
  transition-delay: .1s;
}
```
*Take some time and play around with the delay and translation for different effects.*

Time for our little icons. 

```css=
.share__button a {
  flex: 1;
  font-size: 26px;
  color: #2d3436;
  text-align: center;
  transform: translateX(-100%);
  opacity: 0;
  transition: .3s linear;
  height: 80px;
  line-height: 80px;
}
```

Flex gives us alot of power for positioning. `flex: 1` will make sure all the elements take up even space within the parent element.

We will now be adding two more hover selctions. One on the button to make the icons appear. And another on the icons themselves to make them grow.

```css=
.share__button:hover a {
  opacity: 1;
  transform: translateX(0);
}

.share__button a:hover {
  transform: scale(1.4);
  color: #f1f1f1;
}
```

Lastly, we will add specific styles for each icon for their color values.

```css=
.share__icon--facebook:hover{
  background: #3b5998;
}

.share__icon--twitter:hover{
  background: #55acee;
}

.share__icon--instagram:hover{
  background: #517fa4;
}

.share__icon--linkedin:hover{
  background: #0077b5;
}
```

And like that you did it! 

![yay!](https://media.giphy.com/media/3oz8xAFtqoOUUrsh7W/giphy.gif)
