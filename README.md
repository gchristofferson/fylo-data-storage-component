# Frontend Mentor - Fylo data storage component solution

This is a solution to the [Fylo data storage component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/fylo-data-storage-component-1dZPRbV5n). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
    - [The challenge](#the-challenge)
    - [Screenshot](#screenshot)
    - [Links](#links)
- [My process](#my-process)
    - [Built with](#built-with)
    - [What I learned](#what-i-learned)
    - [Continued development](#continued-development)
    - [Useful resources](#useful-resources)
- [Author](#author)



## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size

### Screenshot

![](./images/screenshot.jpg)


### Links

- Solution URL: [https://github.com/gchristofferson/fylo-data-storage-component](https://github.com/gchristofferson/fylo-data-storage-component)
- Live Site URL: [https://gchristofferson.github.io/fylo-data-storage-component/](https://gchristofferson.github.io/fylo-data-storage-component/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow
- BEM methodology


### What I learned

Some of my major learnings while working through this project were how to center an absolute positioned element, how to style a progress bar and how to create and position a css triangle.

Here is the css I used to center the info bubble on the mobile layout:
```css
/* First I set position relative on parent container */
.storage__info {
  position: relative;
}

/* Then I center positioned the info bubble */
.storage__info__bubble {
  background-color: #fff;
  color: var(--very-dark-blue);
  padding: 16px 24px;
  max-width: 179px;
  position: absolute;
  margin: 0 auto;
  left: 0;
  right: 0;
  bottom: -36px;
}
```
To get the above to work, I learned having a set width is key.  

On the desktop layout, this same bubble looks like a call-out with a triangle pointer shape in the lower right corner.  Here's the css I used to create and position the shape to create the call-out bubble effect:

```css
.storage__info__bubble::after {
  content: "";
  width: 0;
  height: 0;
  position: absolute;
  border-top: 27px solid transparent;
  border-right: 27px solid #fff;
  border-bottom: 27px solid transparent;
  border-left: 27px solid transparent;
  right: 0;
  bottom: -26px;
}
```
The key to creating triangles is to make a box with 0 width and height, then give one side a border with the width of the final triangle width as well as a solid color.  To get the triangle effect, I had to then set the other 3 sides to the same width and style, but I gave them transparent colors. This produced a triangle, which I then positioned in the bottom right corner of the bubble.

Styling the progress bar was more complicated than I anticipated, but it was fun learning.  What I learned is that in order to style the progress bar, I had to select `progress[value]`.  Then, because of browser inconsistencies I had to reset the default values to 'none' and give the bar a width and height:
```css
.storage__info__used[value] {
    /* Reset the default appearance */
    -webkit-appearance: none;
    appearance: none;

    width: 100%;
    height: 20px;
    position: relative;
}
```
Next I had to style the progress bar itself, or the background:
```css
.storage__info__used[value]::-webkit-progress-bar {
    background-color: var(--very-dark-blue);
    border-radius: 10px;
    padding: 3px;
}
```
Lastly I styled the value bar inside and added the little circle markee at the end of the value using the `::after` pseudo element:
```css
.storage__info__used[value]::-webkit-progress-value {
    background-image: var(--gradient);
    border-radius: 8px;
}

.storage__info__used[value]::after {
    content: '';
    width: 10px;
    height: 10px;
    position: absolute;
    border-radius: 50%;
    right: calc(19% + 2px);
    top: 5px;
    background-color: #fff;
}
```


### Continued development

I tried animating the progress bar value, but had trouble figuring that out.  I definitely want to learn more about how to animate progress bars in my future projects.

### Useful resources

- [How to center a "position: absolute" element](https://stackoverflow.com/questions/8508275/how-to-center-a-position-absolute-element#) - Thanks to stackoverflow, I was able to center my absolute positioned info bubble.  
- [The HTML5 progress Element](https://css-tricks.com/html5-progress-element/) - This is an amazing article by CSS Tricks which helped me style my progress bar. I'd recommend it to anyone still learning this concept.
- [CSS Triangle](https://css-tricks.com/snippets/css/css-triangle/) - Loved this article on creating a CSS triangle.  The codepen.io demo is what drove the point home for me and helped me finally understand how to create a triangle.

## Author

- Frontend Mentor - [@gchristofferson](https://www.frontendmentor.io/profile/gchristofferson)
- Twitter - [@GreggChristoff2](https://twitter.com/GreggChristoff2)



