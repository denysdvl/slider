### This is an  slider <h2>
        
_You **can** combine this with your web project_

here you create variables and re-create elements from your html,
the **slidesIndx** variable is equal to 1 to set the beginning of the slider from the first picture 

```javascript
	 let slidesIndx = 1,
        slider = document.querySelectorAll(".slider-item"),
        prev = document.querySelector(".prev"),
        next = document.querySelector(".next"),
        dotsWrap = document.querySelector(".slider-dots"),
        dots = document.querySelectorAll(".dot");
```

in this function we check for the slide index and if it is greater than our 
slider length we set it to 1 if less than 1 we assign values to the slider length 
to make the transition between 1 and the last element.
Then we hide all the slides and delete the dotted line class 
and at the end we show the actual slide and assign the dotted line class to activate  

```javascript
	function showSlid(num) {
        if (num > slider.length) {
            slidesIndx = 1;
        }
        if (num < 1) {
            slidesIndx = slider.length;
        }

        slider.forEach((item) => item.style.display = 'none');
        dots.forEach((item) => item.classList.remove('dot-active'));
        slider[slidesIndx - 1].style.display = 'block';
        dots[slidesIndx - 1].classList.add('dot-active');
    }
```
in these functions we pass the actual slide number into the **showSlid(num)** function 


```javascript
    function plusItem(num) {
        showSlid(slidesIndx += num);
    }

    function cuurentSlid(num) {
        showSlid(slidesIndx = num);
    }
```
here we process the next and previous arrow clicks
and dots clicks and pass the slide index that should be visible 

```javascript
prev.addEventListener('click', () => {
        plusItem(-1);
    });
    next.addEventListener('click', () => {
        plusItem(1);
    });
    dotsWrap.addEventListener('click', (event) => {
        for (let i = 0; i < dots.length + 1; i++) {
            if (event.target.classList.contains('dot') && event.target == dots[i - 1]) {
                cuurentSlid(i);
            }
        }
```


*to use this feature just copy the code from the project and paste it into your project.*
