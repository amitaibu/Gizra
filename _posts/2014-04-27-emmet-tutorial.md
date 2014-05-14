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
Some of you may know it as “Zen coding” and for quite some time (Since 2012) it’s known as <a href="http://emmet.io/">Emmet</a>.

Emmet is a plugin for a text editor which greatly improves html and css workflow.   
The idea behind it is to instantly expand simple abbreviations into complex code snippet.   
The creator of Emmet is <a href="http://emmet.io/credits/">Sergey Chikuyonok</a>.   
It’s available for many popular text editors such as: Sublime text, Phpstrom, Eclipse, Aptana, TextMate, Coda, Nodepad++ and many more.

**For those who don’t know what an abbreviation is ?**
Abbreviation It’s a shortened form of a word or phrase. Usually, but not always, it consists of a letter or group of letters taken from the word or phrase.   
Emmet use these abbreviations to parse them in runtime and transform them into structured code block, HTML, CSS, XSL or any other structured markup.
This tutorial will mainly review the abbreviations of the html and a little bit of the css.
* For the official <a href="http://docs.emmet.io/">Emmet documentation</a>.
* For the complete list of available abbreviations use the official <a href="http://docs.emmet.io/cheat-sheet/">cheat sheet</a>.

Let’s move on to the examples and let the cool part begin ;)

this abbreviation:
```
div#wrapper>div.box+ul#navigation>li*5>a{Item $}
```

* To expand this abbreviation into a structured html we need to press the ```tab``` key.
Every IDE that uses emmet plugin may have a different key configuration, most of them uses the tab key.

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

#### Generating html with Emmet.

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

* There is no limit  to the numbers of attributes you can define.
* Attributes don't have to include a value, ``` div[title style]``` will transform into ```<div title="" style=""></div>```.
* Supports "tabstops" inside every empty attributes (will be covered later in this tutorial).


#### Text ```{}```
The curly braces enables the adding of text to an element.

this abbreviation:
```
div>p{some random text}
```

will be transformed into:
```html
<div>
  <p>some random text</p>
</div>
```

* Emmet has a nice feature to generate a dummy text it's called the Lorem Ipsum generator.

this abbreviation:
```
p>lorem
```

will be transformed into:
```html
<p>
Lorem ipsum dolor sit amet, consectetur adipisicing elit. Esse nisi pariatur
perferendis, quod ratione similique soluta. A animi consequatur ipsa labore
omnis perspiciatis quo sequi ut. Asperiores corporis repellat suscipit?
</p>
```

* We can add a number to control the amount of words been generated.

this abbreviation:
```
p>lorem5
```

will be transformed into:
```html
<p>Lorem ipsum dolor sit amet.</p>
```

#### Item numbering ```$```
This ```$``` operator can be used to add numbers.
It could be used to number an element name, attribute or value.

this abbreviation:
```
ol>li.class$*3
```

will be transformed into:
```html
<ol>
  <li class="class1"></li>
  <li class="class2"></li>
  <li class="class3"></li>
</ol>
```

this abbreviation:
```
ol>li{text: $$$}*3
```

will be transformed into:
```html
<ol>
  <li>text: 001</li>
  <li>text: 002</li>
  <li>text: 003</li>
</ol>
```

##### This ```@N``` operator controls the base value.

this abbreviation:
```
ol>li.class-$@10*3
```

will be transformed into:
```html
<ol>
  <li class="class-10"></li>
  <li class="class-11"></li>
  <li class="class-12"></li>
</ol>
```

##### This ```@-``` operator controls the sort order of the numbers (ascending/descending)

this abbreviation:
```
ol>li.class-$@-*3
```

will be transformed into:
```html
<ol>
  <li class="class-3"></li>
  <li class="class-2"></li>
  <li class="class-1"></li>
</ol>
```

It's also possible to combine both operators.

this abbreviation:
```
ol>li.class-$@-8*3
```

will be transformed into:
```html
<ol>
  <li class="class-10"></li>
  <li class="class-9"></li>
  <li class="class-8"></li>
</ol>
```

#### Generating CSS with Emmet.
Emmet has the ability to provide shorthands for CSS properties.
This mean you have an arsenal of predefined snippets for properties.
But that's not all, Emmet also gives you the ability to define values for these properties as you declare the abbreviation.
If you want to view the complete list of available snippets go to the css section of the official cheat sheet (the link is at the first section of this tutorial).


Lets say that you want to add a ```margin``` property to "some-class" and you want the ```top + bottom  = 10px``` and the ```right + left = 5px```.

this abbreviation:
```
.some-class {
  m10-5
}
```

will be transformed into:
```css
.some-class {
  margin: 10px 5px;
}
```
If we examine the syntax we can see we have the first letter of the property ```m = margin``` and right next to it we supply the values we want separated by hyphens.

##### Emmet's measuring units.
* Default measuring unit for integers is ```px```.
* Default measuring unit for floats it's ```em```.
* When explicitly defining units, you don’t need to use hyphens to separate values.
* You can define other units as you like (can use the full name or use Emmet's value aliases.
   * p => %
   * e => em
   * x => ex

this abbreviations:
```
.some-class {
  m5e10p15x20pt
}
```

will be transformed into:
```css
.some-class {
  margin: 5em 10% 15ex 20pt;
}
```

* In order to define a negative value for the property, all you need to do is add a hyphen before to the value ```-```.

this abbreviations:
```
.some-class {
  m5--10
  p5p-10p
}
```

will be transformed into:
```css
.some-class {
  margin: 5px -10px;
  padding: 5% -10%;
}
```

##### Color values

* Emmet has a built in support for hex color values. You can use the short notation and supply one, two, three or six characters as color value.

this abbreviations:
```
.some-class {
  c#f
  c#f5
  c#fc0
  c#d2047d
}
```

will be transformed into:
```css
.some-class {
  color: #ffffff;
  color: #f5f5f5;
  color: #ffcc00;
  color: #d2047d;
}

Lets say that you want to add a ```border``` property to my "some-class" and you want the ```width  = 2px``` and the ```color = #000000 (Black)```.

this abbreviations:
```
.some-class {
bd2#0
}
```

will be transformed into:
```css
.some-class {
  border: 2px #000000;
}







