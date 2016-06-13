Line 10
```
(ellipse 100 100 30 30)
```

`ellipse` is a function, an instruction.
We tell clojure to perform this instruction by putting it inside parentheses `(` and `)`. We refer to this as "calling a function".
We follow this instruction with 4 options, known as "parameters", for the x y coordinates on the screen 100 100 and the size of the ellipse (it's horizontal and vertical radius) 30 30.
Try changing the arguments to other numbers, running the sketch again, and see what happens. Can you make a bigger circle or move it lower down the picture?


Lines 8:10
```
(background 255)
(fill 192)
(ellipse 100 100 30 30)
```

This call to ellipse takes place alongside three other function calls.
The first sets the background to be white (255 is white, 0 is black).
The second sets the colour with which we fill any shapes that follow (192 is grey).
Try changing the colours. If you give 3 arguments instead of 1 you can get Red-Green-Blue colours, instead of greyscale (e.g. `(fill 64 0 192)`.


Lines 7:10
```
(defn draw []
  (background 255)
  (fill 192)
  (ellipse 100 100 30 30))
```

Each of these function calls are made inside another function call. Can you see which it is?
The `defn` function is used to define functions - or to make new ones. Here we're defining a function called `draw`.
The first argument to `draw` is `[]`. That's a vector - or list - that explains what arguments the function takes. `draw` takes no arguments so the vector is empty.
If you like you can go off and [find out more about vectors](#todo) then come back when you're ready. Or you can just accept what this is for now and worry about vectors when you need them!

```
(defn draw []
  (background 255)
  (fill 255 0 0)
  (ellipse 50 50 40 40)
  (fill 192)
  (ellipse 100 100 30 30))
```
The draw function is run by quil, over and over in a loop. You can add other function calls to the draw function.
The version above adds in a bright red circle. Notice that each line has one open parenthesis `(` and one closing one `)` except for the first line which has no closing parenthesis and the last line which has two. That's because all the lines in between are inside the "body" of the `draw` function. The second closing parenthesis on the last line completes the definition of `draw`.
At this point you should try experimenting with the other functions you can include in the draw loop. You might like to have a look at the [quil cheatsheet](#todo) for a taster of whats available or the [index of functions](http://quil.info/api) for a complete description.