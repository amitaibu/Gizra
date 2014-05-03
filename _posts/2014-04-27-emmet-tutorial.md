---
title: Introducing Emmet!
tags:
- Emmet
- tutorial
- html
- css
permalink: /content/emmet-tutorial/
created: 1398453017
layout: post
published: false
---

#### Did you ever wanted to create an “instant” html and css ?
If you answered “yes” then you are in the perfect place to meet the ultimate tool that will enhance your productivity and save you a lot of time when coding.
Some of you may know it as “Zen coding” and for quite some time (2012) it’s known as <a href="http://emmet.io/">Emmet</a>.

Emmet is a plugin for a text editor which greatly improves html and css workflow.   
The idea behind it is to instantly expand simple abbreviations into complex code snippet.   
The creator of Emmet is <a href="http://emmet.io/credits/">Sergey Chikuyonok</a>.   
It’s available for many popular text editors such as: Sublime text, Phpstrom, Eclipse, Aptana, TextMate, Coda, Nodepad++ and many more.

For those who don’t know what an abbreviation is ?
Abbreviation It’s a shortened form of a word or phrase. Usually, but not always, it consists of a letter or group of letters taken from the word or phrase.   
Emmet use these abbreviations to parse them in runtime and transform them into structured code block, HTML, CSS, XSL syntax.
This tutorial will mainly review the abbreviations of the html and a little bit of the css.
for the complete list of available abbreviations use the official <a href="http://docs.emmet.io/cheat-sheet//">cheet sheet</a>
.   
Let’s move on to the examples and let the cool part begin ;)

this abbreviation:
```
div#wrapper>div.box+ul#navigation>li*5>a{Item $}
```
will be transformed into:
```html
<div id="wrapper">
  <div class="box"></div>
  <ul id="navigation">
    <li><a href="">Item 1</a></li>
    <li><a href="">Item 2</a></li>
    <li><a href="">Item 3</a></li>
    <li><a href="">Item 4</a></li>
    <li><a href="">Item 5</a></li>
  </ul>
</div>
```

If we examine the syntax we can see it’s mainly constructed out of ”html tags” and “css selectors” alongside special characters that bounds the connection (logic) between them.   
This makes it easy to use for any one who knows html and css, specially web developers.

Emmet is very flexible and can be expanded to meet your needs by allowing you to:
(this things are beyond the scope of this tutorial).
* Add your own or update existing snippets.
* Change behavior of some Emmet filters and actions.
* Define how generated HTML/XML should look.



### Nesting operators:
Nesting operators are used to position the abbreviation in the structured tree.

#### Child: ```>```
Use the > operator to nest elements inside each other.

this abbreviation:
```
div.grandparent>div.parent>div.child
```
will be transformed into:
```html
<div class="grandparent">
  <div class="parent">
    <div class="child"></div>
  </div>
</div>
```

#### Siblings: ```+```
Use the + operator to place elements on the same level base - near each other.

this abbreviation:
```
header+section+footer
```
will be transformed into:
```html
<header></header>
<section></section>
<footer></footer>
```
#### Climb up: ```^```
Use the ^ operator to climb one level up and place the element in that position.
You can use as many ^ operators as you want, this gives you the ability to move several levels up.

this abbreviation:
```
section.top+section.middle>p^section.bottom
```
will be transformed into:
```html
<section class="top"></section>
<section class="middle">
  <p></p>
</section>
<section class="bottom"></section>
```

#### Multiplication: ```*```
Use the * operator define how many times this element will be outputted.

this abbreviation:
```
ul>li*3
```
will be transformed into:
```html
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```
#### Grouping: ```()```
Use the () operator to group subtrees in complex abbreviations, This gives you an easier
control of the elements position in the structured tree.

this abbreviation:
```
div.wrapper>(header>ul>li.item*2>a)+section.main+footer
```
will be transformed into:
```html
<div class="wrapper">
  <header>
    <ul>
      <li class="item"><a href=""></a></li>
      <li class="item"><a href=""></a></li>
    </ul>
  </header>
  <section class="main"></section>
  <footer></footer>
</div>
```
* You can nest groups inside each other combined with the multiplication * operator.

this abbreviation:
```
table>(tr>(td.name+td.age))*2
```
will be transformed into:
```html
<table>
  <tr>
    <td class="name"></td>
    <td class="age"></td>
  </tr>
  <tr>
    <td class="name"></td>
    <td class="age"></td>
  </tr>
</table>
```

### Attribute operators:
This operators are used to modify attributes of outputted elements.

#### ID and CLASS:
To define an ID or CLASS to an element you use the already known notation for a CSS selector.
* ID operator is ```#```
* CLASS operator is ```.```

this abbreviation:
```
div#header+div.wrapper>div.class1.class2
```
will be transformed into:
```html
<div id="header"></div>
<div class="wrapper">
  <div class="class1 class2"></div>
</div>
```

#### Custom attributes:
To define an attribute to an element you use the already known notation we use in CSS for attributes.
* Attribute is defined inside the ```[]```

this abbreviation:
```
div[title="sample title" style="color: green;"]
```
will be transformed into:
```html
<div title="sample title" style="color: green;"></div>
```

* You define as many attributes as you like inside the square brackets.
* Attributes don't have to include a value, ``` div[title style]``` will transform into ```<div title="" style=""></div>```.
* Supports "tabstops" inside every empty attributes (will be covered later in this tutorial).

### Item numbering ```$```
Use the $ operator cab be used to number anything you want. Emmet will find the first occurrence
of this $ and will auto increment(the increment dependence on various variables that you can pass). you can place it any where you want.

this abbreviation:
```
div>ol>li.item-$*4
```
will be transformed into:
```html
<div>
  <ol>
    <li class="item-1"></li>
    <li class="item-2"></li>
    <li class="item-3"></li>
    <li class="item-4"></li>
  </ol>
</div>
```
