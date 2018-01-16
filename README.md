# [Slide in on Scroll](https://gk-hynes.github.io/slide-in-on-scroll/)

[![Screenshot of Slide in on Scroll page](https://res.cloudinary.com/gerhynes/image/upload/v1516049515/SlideInOnScroll_gye8fd.jpg)](https://gk-hynes.github.io/slide-in-on-scroll/)

## Notes

Select all the images you are going to listen for. By deafult they are hidden slightly offscreen, have an opacity of 0 and are scaled at 95%.

When they are scrolled half into view a class of `active` is applied, `translateX` returns them to 0, and they are scaled back up.

First, create a function, `checkSlide`, that will run every time the user scrolls. Listen for a scroll on the window and run this function.

Use a `debounce` function to guarantee that you will only run `checkSlide` at most every 20 milliseconds (to protect performance).

Inside `checkSlide`, loop over every image and figure out where it needs to be shown.

Use `window.scrollY`, to figure out how far the page is being scrolled down, and add `window.innerHeight` to work out where the bottom of the window is.

Then subtract `sliderImage.height / 2` to find the middle of the image.

```js
const slideInAt = window.scrollY + window.innerHeight - sliderImage.height / 2;
```

`sliderImage.offsetTop` will tell you how far the top of the image is from the top of the window. Then add `sliderImage.height` to find out where the bottom of the image is.

```js
const imageBottom = sliderImage.offsetTop + sliderImage.height;
```

Put `sliderImage.offsetTop`and `window.scrollY` into their own variables to make the subsequent if statment easier to read.

```js
const isHalfShown = slideInAt > sliderImage.offsetTop;
const isNotScrolledPast = window.scrollY < imageBottom;
```

If the image is half shown and not scrolled past add a class, `active`. Otherwise, remove that class.

```js
if (isHalfShown && isNotScrolledPast) {
  sliderImage.classList.add("active");
} else {
  sliderImage.classList.remove("active");
}
```
