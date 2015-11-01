## Website Performance Optimization portfolio project

### Pizza Perf Project

#### views/css/style.css
Added will-change to the  mover  class so that each movable pizza got its own layer. Going to address the number of pizzas in the JS file to avoid bloating the memory:
will-change: transform;

#### views/js/main.js

##### sizeSwitcher()
* Changed to just convert the size slider value into a sizePercentage to use for the calculation of the size changing.

##### determineDx()
* Eventually removed this function and simplified the calculations in the calling function changePizzaSizes().

##### changePizzaSizes()
* Moved the use of document.querySelectorAll(".randomPizzaContainer") out of the for loop at put it before the loop.
* Removed the call to determineDx() and instead used the figured out sizePercentage based on the slider.

##### changeSliderLabel()
* Moved the document.querySelector("#pizzaSize") call out of the function and saved the results ahead to avoid it getting called multiple times.

##### updatePositions()
* Moved the call to document.getElementsByClassName("mover") outside the function since this is only needed once.
* Moved the call to document.body.scrollTop out of the loop.
* Split the for loop into 2 separate loops. The first one to use attribute basicLeft and store it for all the elements we need. The 2nd loop applies the changes to all the elements, thus removing the forced layout change. I created a dictionary for the temporary data and then re-used that collection in the 2nd loop:
+    data[i].item.style.left = data[i].style_left;
Setting style.left would cause a layout change, and the data[i].style_left is my made up variable that has the value from the previous loop.


##### addEventListener()
* Moved the document.querySelector("#movingPizzas1") call out of the loop.
* Changed the loop from creating 200 pizzas to just 20 to be more reasonable and reduce memory usage since we are making a layer for each one.
* Removed the call to updatePositions() because it seemed unnecessary in the loading part since it will run anyway when it's scrolled. 

#### views/pizza.html
* Changed to use a smaller version of the pizzeria image.
