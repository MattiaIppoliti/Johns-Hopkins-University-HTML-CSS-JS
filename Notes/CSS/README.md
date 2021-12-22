# CSS
_Tip_: Good resources: 
- [cssreference.io](https://cssreference.io/): Collection of all 129 CSS properties
- [Bible](https://developer.mozilla.org/en-US/docs/Web/CSS): Everything about CSS
- [Bible Github](https://github.com/mdn/content/tree/main/files/en-us/learn/css): MSN GitHub repo
- [Awesome Learning CSS](https://github.com/micromata/awesome-css-learning): How to learn + Tool
- [w3school](https://www.w3schools.com/default.asp)

##  Table-of-Contents
- [1. CSS](#1.2-css-General)
- [2. Class & Id](#2.Class-&-Id)
- [3. Responsive Design](#3.Responsive-Design)

## 1.1 So what's CSS?
**Cascading Style Sheets** (**CSS**) is a [stylesheet](https://developer.mozilla.org/en-US/docs/Web/API/StyleSheet) language used to describe the presentation of a document written in [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML "HyperText Markup Language") or [XML](https://developer.mozilla.org/en-US/docs/Web/XML/XML_introduction). CSS describes ==how elements should be rendered on screen, on paper, in speech, or on other media==. The web would be a boring place if all websites looked only with HTML. Using CSS you can control exactly how HTML elements look in the browser, presenting your markup using whatever design you like.

## [Properties and values](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured#properties_and_values "Permalink to Properties and values")

At its most basic level, CSS consists of two components:

-   **Properties**: These are human-readable identifiers that indicate which stylistic features you want to modify. For example, [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size), [`width`](https://developer.mozilla.org/en-US/docs/Web/CSS/width), [`background-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color).
-   **Values**: Each property is assigned a value. This value indicates how to style the property.

The example below highlights a single property and value. The property name is `color` and the value is `blue`.

![A declaration highlighted in the CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/How_CSS_is_structured/declaration.png)

When a property is paired with a value, this pairing is called a _CSS **declaration**_. CSS declarations are found within _CSS Declaration Blocks_. In the example below, highlighting identifies the CSS declaration block.
![[Pasted image 20211219175935.png]]

## 1.2-CSS-General

CSS is a rule-based language — you define rules specifying groups of styles that should be applied to particular elements or groups of elements on your web page. For example "I want the main heading on my page to be shown as large red text."

The following code shows a very simple CSS rule that would achieve the styling described above:

```css
h1 {
    color: red;
    font-size: 5em;
}
```

The rule opens with a selector . This _selects_ the HTML element that we are going to style. In this case we are styling level one headings (`<h1>`).

We then have a set of curly braces `{ }`. Inside those will be one or more **declarations**, which take the form of **property** and **value** pairs. Each pair specifies a property of the element(s) we are selecting, then a value that we'd like to give the property.

_**Note**_: Outside the *.html* file, We can also create a file named: `style.css`, and inside it, given the fact that we are on the same folder inside the pc, we can put the actual code of the entire style of the page.
![[Pasted image 20211216131753.png|200]]
```html
<link rel="stylesheet" href="style.css">
```
If the style file is in another folder we can write: `name-of-the-folder/style.css`.

_**Tip**_: Given the fact that CSS is a **Cascade** style, It's good practice to have ==internal style after global styles==, because, usually, the internal one wants to be more specific then the external ones that are applied to multiple pages inside the site.
```html
<head>
	<link rel="stylesheet" href="style.css">
	<style>
		body {
			background-color: black;
			color: white;
			}
	</style>
</head>
```


#### 1.2.1 Conflict Resolution
- When two declarations are **in conflict**, in other words they specify the same property for the same target, origin precedence rule kicks in, and it's a very simple rule. And the rule is, ==the last declaration wins==. That means top to bottom. So as you see the declarations happen, the lower on the page they are, the more precedence they have.
- When different CSS declarations do **not conflict**, that is, they still target the same element, but the CSS properties with which they target that element are different, there's even a simpler rule. And that is that ==declarations merge==. *Example*: a declaration for, for example, font size, and a declaration for color, since they're two different properties, when they're targeted to the same element, even if they're targeted from two different origins, they will merge into one. And the element will get both the font size and the color.
- **Ineritence**: The basic idea is that you have the document object model tree. And if you specify some CSS property on some element, all the children and grandchildren and so on and so on of that element will also inherit that property without you having to specify the property for each and every element.
	![[Pasted image 20211217111746.png|500]]
- **Specificity**: Most specific selector combinators wins: cosider specificity as a score, the selector with highest core, wins. 
	![[Pasted image 20211217115136.png|300]]       ![[Pasted image 20211217115153.png|300]]
*Example: ![[Pasted image 20211217115327.png|500]]*
#### 1.2.1 CSS Syntax
![CSS p declaration color red|350](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics/css-declaration-small.png)

The whole structure is called a **ruleset**. (The term _ruleset_ is often referred to as just _rule_.) Note the names of the individual parts:
- [Selector](#selector): `p {...}`, element(s) to be styled.
- Declaration: `color:red`, It specifies which of the element's **properties** you want to style.
- Properties: `color`, ways in which you can style an HTML element.
- Property value: `red`, it chooses one out of many possible appearances for a given property.

To modify multiple property values in one ruleset, write them separated by semicolons, like this:

```css
p {
  color: red;
  width: 500px;
  border: 1px solid black;
}
```

You can also select multiple elements and apply a single ruleset to all of them. Separate multiple selectors by commas. For example:

```css
p, li, h1 {
  color: red;
}
```


#### Selector 

This is the HTML element name at the start of the ruleset. It defines the element(s) to be styled (in this example, [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) elements). To style a different element, change the selector. 

Here are some of the more common types of selectors:

| Selector name                                              | What does it select                                                                                                                       | Example                                                                                   |
| ---------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Element selector (sometimes called a tag or type selector) | All HTML elements of the specified type.                                                                                                  | `p`  <br> selects `<p>`                                                                   |
| ID selector                                                | The element on the page with the specified ID. On a given HTML page, each id value should be unique.                                      | `#my-id` <br>  selects `<p id="my-id">` or `<a id="my-id">`                               |
| Class selector                                             | The element(s) on the page with the specified class. Multiple instances of the same class can appear on a page.                           | `.my-class` <br>  selects `<p class="my-class">` and `<a class="my-class">`               |
| Attribute selector                                         | The element(s) on the page with the specified attribute.                                                                                  | `img[src]`  <br> selects `<img src="myimage.png">` but not `<img>`                        |
| Pseudo-class selector                                      | The specified element(s), but only when in the specified state. (For example, when a cursor hovers over a link.)                          | `a:hover`  <br> selects `<a>`, but only when the mouse pointer is hovering over the link. |
| Child Combinator                                           | Only a type of element(s) that are directly chirldren to a particular section: *ex*: every **b** elements that is a direct child of *section* | section `>` b, div `>` b { <br>color: blueviolet;<br>}                                        |



The below table gives you an overview of the selectors you have available to use, and we should read it from right to left <--

| Selector                                                                                                                                                      | Example             | Learn CSS tutorial                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Type selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors)                                                                              | `h1 {  }`           | [Type selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors#type_selectors)                   |
| [Universal selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors)                                                                    | `* {  }`            | [The universal selector](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors#the_universal_selector)   |
| [Class selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors): every element that has a `class="box"`                                    | `.box {  }`         | [Class selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors#class_selectors)                 |
| [id selector](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors)                                                                                  | `#unique { }`       | [ID selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Type_Class_and_ID_Selectors#id_selectors)                       |
| [Attribute selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors)                                                                    | `a[title] {  }`     | [Attribute selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Attribute_selectors)                                     |
| [Pseudo-class selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)                                                                     | `p:first-child { }` | [Pseudo-classes](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements#what_is_a_pseudo-class)    |
| [Pseudo-element selectors](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)                                                                  | `p::first-line { }` | [Pseudo-elements](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements#what_is_a_pseudo-element) |
| [Descendant combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Descendant_combinator): every *p* inside an *article* even if is not a direct child | `article p`         | [Descendant combinator](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#descendant_selector)                       |
| [Child combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator): every *p* that is a *direct* child of an *article* element             | `article > p`       | [Child combinator](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#child_combinator)                               |
| [Adjacent sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator)                                                   | `h1 + p`            | [Adjacent sibling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#adjacent_sibling)                               |
| [General sibling combinator](https://developer.mozilla.org/en-US/docs/Web/CSS/General_sibling_combinator)                                                     | `h1 ~ p`            | [General sibling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators#general_sibling)                                 |


## 1.3 Font and texts
We can find other fonts from [Google Fonts](https://fonts.google.com/). This code links your page to a style sheet that ==loads the Open Sans font family== with your webpage.
    
```css
<link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">
```

The property `font-family` refers to the font(s) you want to use for text. This rule defines a global base font and font size for the whole page. 
    
```css
html {
  font-size: 10px; /* px means "pixels": the base font size is now 10 pixels high  */
  font-family: "Open Sans", sans-serif; /* this should be the rest of the output you got from Google fonts */
}
```

 **_Note_:** Anything in CSS between `/*` and `*/` is a **CSS comment**. The browser ignores comments as it renders the code. CSS comments are a way for you to write helpful notes about your code or logic.

## [[1.4 Boxes]]
Something you'll notice about writing CSS: a lot of it is about boxes. This includes setting size, color, and position.  CSS layout is mostly based on the _box model._ Each box taking up space on your page has properties like:
-   `padding`, the space around the content. In the example below, it is the space around the paragraph text.
-   `border`, the solid line that is just outside the padding.
-   `margin`, the space around the outside of the border. By default on any browser it is not set to `0`.
![three boxes sat inside one another. From outside to in they are labelled margin, border and padding|400](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics/box-model.png)

In this section we also use:

-   `width` (of an element).
-   `background-color`, the color behind an element's content and padding.
-   `color`, the color of an element's content (usually text).
-   `text-shadow` sets a drop shadow on the text inside an element.
-   `display` sets the display mode of an element. (keep reading to learn more)



## [[2.Class-&-Id]]

## 2.1 Class
(It's defined with a ==*.*== in front of the name of the class) and we use classes when:
-  we want to **apply the same style to the same elements**.
-  But **Not all elements** of the same name

The most common way to do this is to add a class to your #HTML element and target that class. 

```html
<ul>
  <li>Item one</li>
  <li class="special">Item two</li>
  <li>Item <em>three</em></li>
</ul>
```
In your #CSS file, you can target the class of `special` by creating a selector that starts with a full stop character. Add the following to your CSS file:
```css
.special {
  color: orange;
  font-weight: bold;
}
/* All <li> elements with class="spacious" */
li.spacious {
  margin: 2em;
}
/* All <li> elements with a class list that includes both "spacious" and "elegant" */
/* For example, class="elegant retro spacious" */
li.spacious.elegant {
  margin: 2em;
}
```

*Esempio*:
#CSS
```css
.red {
  color: #f33;
}

.yellow-bg {
  background: #ffa;
}

.fancy {
  font-weight: bold;
  text-shadow: 4px 4px 3px #77f;
}
/* All <p> elements with class="blue" */
p.blue{
	color: blue} 
```
#HTML
```html
<p class="red">This paragraph has red text.</p>
<p class="red yellow-bg">This paragraph has red text and a yellow background.</p>
<p class="red fancy">This paragraph has red text and "fancy" styling.</p>
<p>This is just a regular paragraph.</p>
```

![[Pasted image 20211217100239.png|500]]
[⬆ back to top](#table-of-contents)

## 2.2 Id
It's defined with a ==**# **== in front of the name of the particular value. We can use id when:
- You **don't need to apply the same style to multiple elements**;
- To have an *unique* selector to a common element

In the #HTML file we can write:
```css
<section class="box" id="ids">
```
And in the #CSS file:
```css
#ids {

color: tomato;

}
```

## 3. [[Responsive-Design]]

### 3.1 Media Queries
Media queries allow you to **group styles together and target them to devices based on some criteria**. For example, you can target a device by its width, its height, or orientation like landscape or portrait. Of course one of the most obvious differences between viewing a website on a desktop browser and your cell phone is the screen size. Remember that using CSS you have the power to produce very different web page layouts from the same HTML.

The most common way to adjust the styling and layout of your page is to provide different styles for different screen sizes of the user's devices.

A media query starts with a *keyword @media*, and then it is followed by *a media feature*, and followed by *curly braces*. Within those curly braces you have your styles, it's basically like a style sheet within a style sheet. Each media feature resolves to either true or false. You can have more than one media features combine together using logical operators. If the media features resolve to true, the style within the curly braces apply.

There are quite a bit of these media features that are available. So you can have max-width, you can have min-width, you can have height which is not listed here, you can even target orientation of your device, portrait or landscape, you can target only screens as opposed to targeting only print. Again, if any of these things evaluate to true, the styles contained within the curly braces of the media query will be in effect.
![[Pasted image 20211218105716.png|400]] --> ![[Pasted image 20211218110018.png|250]]

The media features can be combined using logical operators. One of the most common logical operators is the and operator. Another way to combine media features is to place comma in between them which will 
basically translate into being equivalent to an OR operator.
![[Pasted image 20211218110137.png|400]]

*How you structure media queries within your style sheet? * What usually happens is you have a few of these media queries, but you almost always start with some **base styles**. Base styles will apply across the board no matter what screen size you actually are viewing the website on.

![[Pasted image 20211218110351.png|300]]

### 3.2 Responsive Design

Responsive design was born primarily out of the need to deal with the explosion of mobile devices that started being able to browse the web much in the same way that a desktop browser user browsed the web.

*So what is a responsive web site? *
Well, that's a site that's designed to adapt its layout to the viewing environment by using fluid, proportion-based grids, flexible images, and CSS3 media queries. 

_12-column Grid_: The largest part of responsive design is, obviously, the *layout*. And the most common layout out there or responsive layout, is a **12-column grid responsive layout** and this is what Twitter bootstrap uses and just about almost really every responsive framework out there uses nowadays. 

And, the reason 12 is what's used is because of the **factors of 12**. You could basically, t's evenly, nicely** divisible by 1, 2, 3, 4, 6, and obviously 12 itself**, which means, we could sub-divide our page into sections that are evenly split and nicely layout themselves.

We know that the browser window is 100%, right? That's the width of the browser window. Which means that we calculate what one column in this 12 column grid layout is. That's 100% divided by 12. Where, for example, threes into 25% because three columns is 25% of 12 columns. And the 6 columns become 50% of the 12 columns and the 444 becomes 33.33%. 

_Nested_: And obviously we're not limited to having just one 12 grid. We can certainly have **nested** ones so if you have 4 4, 4, and 4. Inside each 4 columns we could consider that 100% and then have another 12-column grid layout inside of it.

![[Pasted image 20211218114511.png|350]]  ![[Pasted image 20211218114538.png|360]]

## 3.3 Example Responsive Design
```css
.row{
	width: 100%;
}
/********** Large devices only **********/
@media (min-width: 1200px) {
.col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
float: left;
border: 1px solid green;
}
.col-lg-1 {
width: 8.33%;
}
...
.col-md-11 {
width: 91.66%;
}
.col-md-12 {
width: 100%;
}
```
Let's take a look at our HTML. We have one single row, and a single row contains eight divs, it can contain eight items, eight divs. Each one has a paragraph that says item 1, 2, 3, 4 all the way to 8. 

What I'm trying to tell the browser is that when it is a large device, I want only the classes with `lg` to apply. And it will happen automatically since the classes with md don't exist according to the browser, when the browsers larger in width then 1200 pixels. When the browser size, or the device size becomes smaller, and it becomes *less than 1200 pixels, or 1199 pixels and lower*, I want the layout to switch to class `col-md-6`. So *my four column lay-out*, as I squeeze the browser and make it narrower, should become a *two column layout*, because I'm now specifying in a smaller device* size six and six instead of three, three, and three.*

Now when the browser size gets to less than 950 pixels, **none of these classes will exist as far as the browser will concern.** And what's going to happen then? Well our divs will no longer be floated because **the floating is only defined inside the media queries **which means* they will behave just like regular block level elements *and they will automatically stack one on top of the other. I  should really have one column with each one of these items stacked one on top of the other.
```css
<div class="row">
<div class="col-lg-3 col-md-6"><p>Item 1</p></div>
<div class="col-lg-3 col-md-6"><p>Item 2 Wow this is cool</p></div>
<div class="col-lg-3 col-md-6"><p>Item 3</p></div>
<div class="col-lg-3 col-md-6"><p>Item 4</p></div>
<div class="col-lg-3 col-md-6"><p>Item 5 This is cool</p></div>
<div class="col-lg-3 col-md-6"><p>Item 6</p></div>
<div class="col-lg-3 col-md-6"><p>Item 7</p></div>
<div class="col-lg-3 col-md-6"><p>Item 8</p></div>
</div>
```

But if we use an iphone 6 we get this:
![[Pasted image 20211218125148.png|200]]
This is because smartphone, they try to zoom out on websites that don't tell them to do anything different. So, they could try to fit the entire content into the viewport of the phone. 

*But How do we tell the phone's browser that, no, this is actually a responsive website and you don't need to try to zoom out, just stay at the regular zoom level? *The way that we do that is by specifying a special `meta` tag.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
What we need to tell it is, that the content of our viewport, is first of all, consider its width to be device width, don't try to zoom out and also, its initial scale to be one.
So, now with this meta tag in place, the browser will consider the** device width as the width of the viewport and its initial scale factor will be one, meaning it won't scale anything up or down.**

## 4.1 Bootstrap

Bootstrap is the most popular HTML, CSS, and JavaScript framework for developing responsive, mobile first projects on the web.

The purist approach, which says you code your mobile version first. And the claim is that it really helps your content strategy. How are you going to lay out your content, what the content should be.
![[Pasted image 20211218175407.png|500]]
- First of all, your Bootstrap grid always has to be inside of a **container wrapper**. 

	There are a couple of choices for that: One, you could use the container class or you could use the container fluid class. 
	- The **container fluid class **stretches your layout the full width of the browser and *provides consistent padding* around your grid and other content.
	- **Regular container** class has **predetermined fixed width** that is still responsive based on the width of the browser. In other words, it has certain width of one break point, a different width at a different break point and so on.

- The next component of the grid is the row. So the row class creates horizontal groups of columns which means that the columns collapse and interact with each other as a group but independently from columns in another row. 
The row class also creates a negative margin, to counteract the padding that the container class sets up. Now why is that done? Well, each column already has its own padding because we want to visually separate columns from each other. If negative margin wasn't applied to the row, the padding of the container would then be in addition to the padding of the edge column. So the content of the column will no longer align nicely with the rest of the content outside of the grid. Where the line of the column content starts and where the line of the regular content starts, you'll see that they don't match.Bootstrap implements that basic design principle for you so you don't trip up.
![[Pasted image 20211218175825.png|300]]     --> ![[Pasted image 20211218174809.png|350]]
-**Columns**: `col-SIZE-SPAN`: 
	- First of all the `size`, it is **screen width range identifier** and it's something like `MD` for medium, `LG` for large, and so on. So, for example, `LG` is defined as 1200 pixels and above. And what that means is that columns will collapse, in other words they'll stack one upon each other, below that width. That is all unless there's another rule that applies. But if you have specified a md or medium, medium size of the screen, that then will kick in, and that will apply.
	- `span`: how many columns the element should span. So the values are from 1 to 12. And what that means is the second the columns will adapt to 12, so 	if you specify let's say, 4, 4, and 4 then it will load up to 12.
	
## Grid options[](https://getbootstrap.com/docs/5.1/layout/grid/#grid-options)

Bootstrap’s grid system can adapt across all six default breakpoints, and any breakpoints you customize. The six default grid tiers are as follow:

-   Extra small (xs)
-   Small (sm)
-   Medium (md)
-   Large (lg)
-   Extra large (xl)
-   Extra extra large (xxl)

As noted above, each of these breakpoints have their own container, unique class prefix, and modifiers. Here’s how the grid changes across these breakpoints:
![[Pasted image 20211219173903.png]]
