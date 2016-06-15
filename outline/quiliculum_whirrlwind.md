# A whirlwind tour of Clojure

This tour provides an introduction to programming with Clojure.  It is designed to prepare you for making sketches with Quil.

The tour is composed of sections. Each section has a few lines of code and a few lines of description. The code should demonstrate some ideas and the description provides names to help you understand and talk about the code. We'll introduce new terms with italics like this: *blah* and refer to quotes from the code like this: `blah`.

You should already have a Clojure *environment* set-up on your computer - that is to say you'll have Java installed and Leiningen.

The code should be *executed* (run) and explored as you go. You should start the *REPL* and feed it the code one line at a time. The word REPL stands for read, evaluate, print, loop and describes what will happen:

1. Your code will be *read* by the machine
2. The instructions in your code will be *evaluated* - if you've added 2 and 3 then the sum will be calculated 
3. The result (5) will be *printed* back out to the screen
4. The process will *loop* back to step 1.

Now it's time to load up the REPL and start typing.

## Forms, Functions and  Arguments
```clojure
(println "Hello World")
```
- `println` is a *function*
- `"Hello World"`, a *string* of text characters, is the function's *argument*
- the whole thing, including the parentheses is a *form*
- we have just *called* the `println` function

##  Infix notation
```clojure
(+ 1 1)
(+ 1 1 1)
(+ 3 (* 2 1))
```
- the function comes first, unlike in maths - this is `prefix` instead of `infix` notation
- this helps to reduce repetition and make the ordering of operations explicit

## Vectors
```clojure
(vector "zero" "one" "two")
["zero" "one" "two"]
(get ["zero" "one" "two"] 2)
```
- the `vector` function takes any number of arguments and joins the values together in a *collection*
- you can use the `get` function to extract the values back out again (nb: the first value is in position 0)

## Var bindings
```clojure
(def pi 3.14)
pi
```
- the `def` function expects two arguments: a *variable* name and a value
- it *assigns* the value to the variable so you can recall that value by name in future
- you may also hear this refered to as *binding* or *defining* a variable

## Let bindings
```clojure
pi
(let [pi 3.141]
  pi)
pi
(let [e 2.17]
  e)
e
```
- the `let` function assigns a variable temporarily
- it expects pairs of variable names & values
- the value is only available in the forms it encloses
- we call this wrapping a *closure*
- outside of the *closure* the variable returns to it's previous value (or to nothing)

## Functions (anonymous)
```clojure
(fn [x y] (+ x y))
((fn [x y] (+ x y)) 2 3)
```
- the `fn` function creates new functions
- it expects two arguments: a vector of argument names and a form that will *return* a value
- you can use it to *encapsulate* any calculation or process, some values go in and one value comes out

## Functions (bound)
```clojure
(defn add [x y] (+ x y))
(add 2 3)
(defn area-of-square [width] (* width width))
(area-of-square 2)
(defn big? [x] (> 1000 x))
(big? 10)
(big? 12345)
```
- the `defn` function combines a `def` and an `fn` to store a function in a variable
- you can call the function using the variable name

## Hashmaps
```clojure
(def city
  { "name" "berlin",
    "population" 3502000 })
(get city "population")
(city "population")
(keys city)
(vals city)
```
- a *hash map* is a collection, like a vector, but it is formed of pairs
- the left-hand part of the pair is it's name or *key* and the right is the value
- you can use them to create a collection of named values

## Keywords
```clojure
:population
(def city { :name "Berlin", :population 3502000 })
(:name city)
(:population city)
```
- a *keyword* is a special type of word
- it's a bit like a string in that it's made of letters
- it can act like a function, and so it's quite convenient for accessing values in hash maps

## Namespaces
```clojure
(ns tools)
(def nail "Small metal spike")
(ns hands)
(def nail "Hard skin on finger tip")
tools/nail
hands/nail
```
- Sometimes we need to reuse the same variable name for different things
- We can distinguish the uses with a *namespace*
- Here we switch namespaces with the `ns` function (note that you were in the `user` namespace by default)
- Namespaces are also useful for grouping together related functions and variables (much like using folders for files)

## Require
```clojure
(clojure.string/join "." ["www" "clojure" "org"])
(ns lauchpad
  (:require [clojure.string :as st]))
(st/join "... " ["3" "2" "1" "Go!"])
```
- Namespaces can be long and tedious to type out all the time
- You can use a `:require` *directive* in your call to `ns` to abbreviate this