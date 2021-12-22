# HTML
It stands for, **Hyper Text Markup Language**.
_Tip_: Usefull Links:
- [HTML-Reference](https://htmlreference.io/): All 113 HTML Elements
## 1.1 Summary
- #Hypertext is text which contains links to other texts and that's basically the entire web
![[Pasted image 20211215152819.png|300]]
- The next term is #Markup. So markup means to mark something up, to annotate. 
![[Pasted image 20211215152714.png|300]]
- #Language basically implies that it has its own syntax meaning there's a right and a wrong way to code it.

So let's talk about the three technologies that drive the web. Each one has its own distinctive purpose and all three of them fit very nicely together.
![[Pasted image 20211215153037.png|300|c]]

- #HTML provides the structure which means what components.For example, it can have one heading, two paragraphs, and a footer. Note that that does not tell you anything about how these components are visually laid out, what they look like, what color they are, what font size they are. 
- The color and style is the role of #CSS. So colors, layouts, font style, font sizes, in other words any stylistic types of things.
- #JavaScript, it's job is to provide behavior, provide functionality. It adds functionality to the page, so for example *what happens when HTML document finishes loading into the browser?*Or what happens if I click on one of the headings?*

## 1.2 So what is HTML?
HTML (**H**yper**t**ext **M**arkup **L**anguage) is the code that is used to structure a web page and its content. For example, content could be structured within a set of paragraphs, a list of bulleted points, or using images and data tables.

HTML is a _markup language_ that defines the structure of your content. HTML consists of a series of **[elements](https://developer.mozilla.org/en-US/docs/Glossary/Element)**, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way. The enclosing [tags](https://developer.mozilla.org/en-US/docs/Glossary/Tag) can make a word or image hyperlink to somewhere else, can italicize words, can make the font bigger or smaller, and so on.  For example, take the following line of content:

My cat is very grumpy

If we wanted the line to stand by itself, we could specify that it is a paragraph by enclosing it in paragraph tags:

```html
<p>My cat is very grumpy</p>
```



## 1.3 Anatomy of an HTML element

Let's explore this paragraph element a bit further.

![|300](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-small.png)

The main parts of our element are as follows:

1.  **The opening tag:** This consists of the name of the element (in this case, p), wrapped in opening and closing **angle brackets**. This states where the element begins or starts to take effect — in this case where the paragraph begins.
2.  **The closing tag:** This is the same as the opening tag, except that it includes a _forward slash_ before the element name. This states where the element ends — in this case where the paragraph ends. Failing to add a closing tag is one of the standard beginner errors and can lead to strange results.
3.  **The content:** This is the content of the element, which in this case, is just text.
4.  **The element:** The opening tag, the closing tag, and the content together comprise the element.

Elements can also have attributes that look like the following:

![](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/grumpy-cat-attribute-small.png)

Attributes contain extra information about the element that you don't want to appear in the actual content. Here, `class` is the attribute _name_ and `editor-note` is the attribute _value_. The `class` attribute allows you to give the element a non-unique identifier that can be used to target it (and any other elements with the same `class` value) with style information and other things.

An attribute should always have the following:

1.  A space between it and the element name (or the previous attribute, if the element already has one or more attributes).
2.  The attribute name followed by an equal sign.
3.  The attribute value wrapped by opening and closing quotation marks.


### 1.3.1 Nesting elements

You can put elements inside other elements too — this is called **nesting**. If we wanted to state that our cat is **very** grumpy, we could wrap the word "very" in a [`<strong>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong) element, which means that the word is to be strongly emphasized:

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```

You do however need to make sure that your elements are properly nested. In the example above, we opened the [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) element first, then the [`<strong>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong) element; therefore, we have to close the [`<strong>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong) element first, then the [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) element. The following is incorrect:

```html
<p>My cat is <strong>very grumpy.</p></strong>
```

The elements have to open and close correctly so that they are clearly inside or outside one another. If they overlap as shown above, then your web browser will try to make the best guess at what you were trying to say, which can lead to unexpected results. So don't do it!

### 1.3.2 Empty elements

Some elements have no content and are called **empty elements**. Take the [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) element that we already have in our HTML page:

```html
<img src="images/firefox-icon.png" alt="My test image">
```

This contains two attributes, ==but there is no closing `</img>` tag and no inner content==. This is because an image element doesn't wrap content to affect it. Its purpose is to embed an image in the HTML page in the place it appears.

### 1.3.3 Anatomy of an HTML document

That wraps up the basics of individual HTML elements, but they aren't handy on their own. Now we'll look at how individual elements are combined to form an entire HTML page. Let's revisit the code we put into our `index.html` example (which we first met in the [Dealing with files](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Dealing_with_files) article):

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <img src="images/firefox-icon.png" alt="My test image">
  </body>
</html>
```

Here, we have the following:

-   `<!DOCTYPE html>` — doctype. It is a required preamble. In the mists of time, when HTML was young (around 1991/92), doctypes were meant to act as links to a set of rules that the HTML page had to follow to be considered good HTML, which could mean automatic error checking and other useful things. However these days, they don't do much and are basically just needed to make sure your document behaves correctly. That's all you need to know for now.
-   `<html></html>` — the [`<html>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/html) element. This element wraps all the content on the entire page and is sometimes known as the root element.
-   `<head></head>` — the [`<head>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head) element. This element acts as a container for all the stuff you want to include on the HTML page that _isn't_ the content you are showing to your page's viewers. This includes things like [keywords](https://developer.mozilla.org/en-US/docs/Glossary/Keyword) and a page description that you want to appear in search results, CSS to style our content, character set declarations, and more.
-   `<meta charset="utf-8">` — This element sets the character set your document should use to UTF-8 which includes most characters from the vast majority of written languages. Essentially, it can now handle any textual content you might put on it. There is no reason not to set this and it can help avoid some problems later on.
-   `<title></title>` — the [`<title>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title) element. This sets the title of your page, which is the title that appears in the browser tab the page is loaded in. It is also used to describe the page when you bookmark/favorite it.
-   `<body></body>` — the [`<body>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/body) element. This contains _all_ the content that you want to show to web users when they visit your page, whether that's text, images, videos, games, playable audio tracks, or whatever else.

## 1.4 Images

It's an Inline element. Let's turn our attention to the [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) element again:

```html
<img src="images/firefox-icon.png" alt="My test image">
```
_Tip_: You can change easly the size of the image using `![[img-link|400]]`.

As we said before, it embeds an image into our page in the position it appears. It does this via the `src` (source) attribute, which contains the path to our image file.

But what should happen when our image doen't load? Or the device the user is using displays only text? We add an alt attribute. We have also included an `alt` (alternative) attribute. In this attribute, you specify descriptive text for ==users who cannot see the image==, possibly because of the following reasons:

1.  They are visually impaired. Users with significant visual impairments often use tools called screen readers to read out the alt text to them.
2.  Something has gone wrong causing the image not to display. For example, try deliberately changing the path inside your `src` attribute to make it incorrect. If you save and reload the page, you should see something like this in place of the image:

![](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics/alt-text-example.png)

The keywords for alt text are "descriptive text". The alt text you write should provide the reader with enough information to have a good idea of what the image conveys.

_Tip_: Width and Height are raccomended to use cause, if a URL of the photo is incorrect, the layout of the page will be the same and will not be broken.
![[Pasted image 20211216093624.png|400]]  ![[Pasted image 20211216093702.png|400]]

## 1.5 Comment
```html
<!-- This is a comment-->
```
## 2.1 HTML Tag

Usually HTML tags have an opening and a closing tag. And they surround some content. In this case, the **tag p**, which stands for paragraph, is communicating to us that the content in the gray area should be treated as a paragraph. 
![[Pasted image 20211215154120.png|300]]
Attribute is a name value pair that is kind of a meta data about the element itself that it's being applied to. So in this example, we are assigning myId as the value of the id attribute. *Each attribute has its own rules for the meaning of its value.*

So for example, id attribute, being assigned as an example, has to be unique within the scope of the entire HTML document. In other words, *no other element* of any kind in the webpage is allowed to have its id attribute equal to the string myID.
![[Pasted image 20211215154301.png|300]]
No space is allowed to exist between the opening bracket and the tag name. And likewise, space is not allowed between the opening bracket and the foreword slash of the closing tag. However, you must have at least one space between the tag itself and any of its attributes, and space is allowed everywhere else and is simply ignored.
_Tip_: We cannot use some character of our keyboard: ![[Pasted image 20211215193143.png|300]]

_Tip2_: If we wnt that some words should be on the same line and not splitted between two different lines we have to use the `&nbsp;`.
 ```html
<victory&nbsp;nor&nbsp;defeat>
```
## 2.2 HTML head and body
#### 2.2.1 Head 
Every HTML page should start with the doc type or document type declaration. The words doc type or HTML could be lower or upper case. This way the browser recognizes that this is a valid .html file. 
 ```html
<!DOCTYPE html>
```
 A #tag is
```
<something here inside>
```
it consists of an opening tag and usually (not every tag has one) a closing tag:
```
</something that was in the opening tag>
```

The #head-tag contains items that describe the main content of the page. Things like what character coding should the browser use for the main content. It can contain authors description of the page, page title, and whatever other external resources are needed to render the page properly, among other things. The point is it contains some #metadata about the main content. 
```html
<head> some code here </head>
```
While not absolutely required, it's always a good idea to specify the character set that the browser should know how to interpret the content of the webpage. The most commonly used character set is #UTF-8. Also note that the meta tag is a stand alone tag. There is no closing meta tag.
```html
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
```

##### The following elements go inside the head element:
> title = what is shown at the tab in your browser  
> style = here we put rules for styling (in another language called CSS)  
> link = links  
> meta =meta information like encoding  
> script = actions for you page  

Most of the things you will want to add (like sentences, pictures, etc) will be added in the body tag. Now lets learn more about them.

#### 2.2.2 Body
After the head tag goes the body tag. The body tag is the root of all content that is visible to the user. It is often referred to as a viewport.
```html
<body> some code here </body>
```

## 2.3 Content Model: Block vs Inline
All elements fall into basically two categories under the traditional content model structure. Either block level elements or inline elements. 


| Block level Elements                                                                         | Inline Elements                                                                                                                                            |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Render to begin on the new line by default.                                                  | Render on the same line by default                                                                                                                         |
| Block-level elements are allowed to contain inline or other block-level elements within them | If you put a whole bunch of in line elements next to each other, they will all be going on on the same line, as if there is no new line character present. |


- #div is a Block Level Elements
- #span is an inline Elements

#### 2.3.1 Block-level Element

A block-level element always starts on a new line and takes up the full width available (stretches out to the left and right as far as it can).
```html
<p>The paragraph is a block-level element.<p>
```
Examples of block-level elements: div h1 - h6 p form

#### 2.3.2 Inline Element

An inline element occupies only the space bounded by the tags that define the inline element. Generally, inline elements may contain only data and other inline elements. The following example demonstrates the inline element's influence:
```html
<p>This <span>span</span> is an inline element</p>
```

#### 2.3.3 Div Element

The div element belongs to the ==block-level group==, often used as a container for other HTML elements. The div element has no required attributes, but both style and class are common. When used together with CSS, the div element can be used to style blocks of content, as we can see in the example below:
```html
<div style="background-color:black;color:white;padding:20px;">
<h2>Lisbon</h2>
<p>Lisbon is the capital city of Portugal.
26.7% of the total population of Portugal lives in the Lisbon Metropolitan Area.</p>  
</div>
```
#### 2.3.4 Span Element

The span element is a generic ==inline container== for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes), or because they share attribute values, such as lang. The span is very much like a div element, but div is a block-level element whereas a span is an inline element.
```html
<h1>My super <span style="color:red">Important</span> Heading</h1>
```

## 2.4 Heading Elements
What does the word semantic mean? 
> definition of semantic is relating to meaning in language or logic. In other words, it has some inherent meaning, the names have some inherent meaning. 

Now when it applies to HTML, what does semantic html element mean? 

>A semantic html element is an element that implies some meaning to the content. In other words, it's an element that tells you something about the content, whether its importance, whether it's a little bit of its description, it basically hints to you to that meaning.

*Esempio*: The heading content between opening h1 and the closing h1 element is the most important heading in the document, and on, and on, and on. So h6 would be also a heading of the document, but it's the least important one of them all.

 ```html
<h1>This is heading 1</h1>
<h2>This is heading 2</h2>
<h3>This is heading 3</h3>
<h4>This is heading 4</h4>
<h5>This is heading 5</h5>
<h6>This is heading 6</h6>
```
Headings are just like paragraphs **BUT** they have different font sizes. h1 is the biggest heading and h6 is the smallest. Search engines use the headings to index the structure and content of your web pages and users skim your pages by its headings.

#### 2.4.1 Simple text formatting tags
 ```html
<b> - Bold text
<strong> - Important text
<i> - Italic text
<em> - Emphasized text
<mark> - Marked text
<small> - Small text
<del> - Deleted text
<ins> - Inserted text
<sub> - Subscript text
<sup> - Superscript text
```



## 2.5 Paragraphs

As explained above, [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) elements are for containing paragraphs of text; you'll use these frequently when marking up regular text content:

```html
<p>This is a single paragraph</p>
```

Add your sample text (you should have it from [_What will your website look like?_](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/What_will_your_website_look_like)) into one or a few paragraphs, placed directly below your [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) element.

## 2.6 Lists

A lot of the web's content is lists and HTML has special elements for these. Lists are an incredibly useful HTML structure that allows you to group related content. Marking up lists always consists of at least 2 elements. The most common list types are ordered and unordered lists:

1.  **Unordered lists** are for lists where the order of the items doesn't matter, such as a shopping list. These are wrapped in a [`<ul>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul) element.
2.  **Ordered lists** are for lists where the order of the items does matter, such as a recipe. These are wrapped in an [`<ol>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol) element.

Each item inside the lists is put inside an [`<li>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li) (list item) element.
#### 2.6.1 Ordered lists

```html
<body>
        <ol>   <!-- Everything between the opening and the closing ol list is taken as a list item -->
            <li> list item 1 </li>  <!-- what is between the opening and closing li is considered a SINGLE list item -->
            <li> list item 2 </li>
            <li> list item N </li>
        </ol>
</body>

By default this list is shown with arabic numbers. We can change this with the type property (that's CSS and we'll talk soon about CSS).
```
#### 2.6.2 Unordered lists
```html
<body>
        <ul>  
            <li> list item 1 </li>  
            <li> list item 2 </li>
            <li> list item N </li>
        </ul>
</body>
```
By default, the list item here are shown with circles in front. If we want to change that, we use the CSS **list-style-type**, which we'll talk about later.

## 2.7 Links

Links are very important — they are what makes the web a web! To add a link, we need to use a simple element — [`<a>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a) — "a" being the short form for "anchor".  the a tag is both a flow content and a phrasing content. In other words, to map it back to the HTML four days, the a tag in the HTML5 is ==both an inline element and a block level element at the same time==. And this is what allows us to take the a tag and surround a div tag inside of it. To make text within your paragraph into a link, follow these steps:

1.  Choose some text. We chose the text "Mozilla Manifesto".
2.  Wrap the text in an [`<a>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a) element, as shown below:
    
    ```html
    <a>Mozilla Manifesto</a>
    ```

    
3.  Give the [`<a>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a) element an `href` attribute, as shown below:
    
    ```html
    <a href="">Mozilla Manifesto</a>
    ```

4.  Fill in the value of this attribute with the web address that you want the link to link to:
    
    ```html
    <a href="https://www.mozilla.org/en-US/about/manifesto/" title="You're clicking in Mozilla webpage">Mozilla Manifesto</a>
    ```

You might get unexpected results if you omit the `https://` or `http://` part, called the _protocol_, at the beginning of the web address. After making a link, click it to make sure it is sending you where you wanted it to.

**Note:** `href` might appear like a rather obscure choice for an attribute name at first. If you are having trouble remembering it, remember that it stands for ***h**ypertext **ref**erence*.

But have you noticed how some links open in the same tab and others for example open in a new tab? This is done with **the target attribute**. The target attribute specifies where to open the linked document and it can have one of the following values:

> _blank - Opens the linked document in a ==new window or tab==
> _self - Opens the linked document in the same window/tab as it was clicked (this is default)  
> _parent - Opens the linked document in the parent frame  
> _top - Opens the linked document in the full body of the window  
> framename - Opens the linked document in a named frame

#### 2.7.1 Create an index to the various sections with link

Another type of link that is extremely important to know about is a #fragment-identifier. It's a # followed by some name like section1, section2, and so on. Now what these links are pointing to is a section of our page. You can have in any tag that has an id with that section name. Notice that the section name does not contain the # sign.Only the link to that section contains the # sign. That's one way to identify a section within the page.
```html
<h1 id="top">Links to Sections of The Same Page</h1>
<section>
<ul>
<!-- Link to every section in the page -->
<li><a href="#section1">#section1</a></li>
<li><a href="#section2">#section2</a></li>
<li><a href="#section3">#section3</a></li>
<li><a href="#section4">#section4</a></li>
<li><a href="#section5">#section5</a></li>
<li><a href="#section6">#section6</a></li>
</ul>
</section>
<section id="section1">
<h3>(#section1) Section 1</h3>
<p>Lorem ipsum dolor sit amet</p>
</section>
```
Another way is to create an anchor tag with a name attribute and name the section very similarly to the way you name a section id. The way you refer to these sections is exactly the same, you put a # in front of the name of the section and stick that value in the href attribute of an anchor tag.
```html
<div>
<h2><a name="section6">(#section6) Section 6</a></h2>
<p>
Back to top: <a href="#top">Back to Top</a>
</p>
</div>
```
The result:
![[Pasted image 20211215195641.png]]
_Tip_: This will be useful for #SPA
## 2.8 Tables

To represent data, we sometimes use tables (Google Spreadsheets, Excel, etc). HTML has tables too and they are quite easy to use.
```html
<table>
  <tr>
    <th>table row 1 first square</th>
    <th>table row 1 second square</th>
  </tr>
  <tr>
    <td>table row 2 first square</td>
    <td>table row 2 second square</td>
    <td>50</td>
  </tr>
  <tr>
    <td>table row 2 first square</td>
    <td>table row 2 second square</td>
  </tr>
</table>
```
An HTML table is defined with the table tag. Each table row is defined with the tr tag. A table header is defined with the tag. By default, table headings are bold and centered. A table data/cell is defined with the td tag.

## 2.9 Classes

Using the html class attribute makes it possible to define equal styles, for elements with the same class name.
```html
<!DOCTYPE html>
<html>
<head>
<style>
div.cities {
    background-color: black;
    color: white;
    margin: 20px 0 20px 0;
    padding: 20px;
}
</style>
</head>
<body>

<div class="cities">
<h2>London</h2>
<p>London is the capital of England.</p>
</div>

<div class="cities">
<h2>Kingston</h2>
<p>Kingston is the capital city of Jamaica.</p>
</div>

<div class="cities">
<h2>Tokyo</h2>
<p>Tokyo is the capital of Japan, the center of the Greater Tokyo Area,
and the most populous metropolitan area in the world.</p>
</div>

</body>
</html>
```
The html class attribute can also be used for inline elements:
```html
<!DOCTYPE html>
<html>
<head>
<style>
span.note {
    font-size: 110%;
    color: blue;
}
</style>
</head>
<body>

<h1>My Ultra <span class="note">Important</span> Heading</h1>
<p>This is some random but <span class="note">important</span> text.</p>

</body>
</html>
```
## 3.1 Buttons

The button tag defines a clickable button.
```html
<button type="button">Click Please</button>
```
These buttons work and behave in exactly the same way as our counterparts above. In addition to submitting the form, you can make them disabled, add an accesskey or even specify a tabindex. The coolest thing about the tag is that you can put useful HTML elements inside them, like images:
```html
<button type="submit"><img src="" alt="" /> Submit</button>
```
"Buttons created with the **BUTTON** element function just like buttons created with the **INPUT** element, but they offer richer rendering possibilities: the **BUTTON** tag may have content. For example: a **BUTTON** element that contains an image functions like and may resemble an **INPUT** element whose type is set to “image”, but the **BUTTON** element type allows content." W3
```html
<div class="buttons">
    <button type="submit" class="positive">
        <img src="/images/icons/tick.png" alt=""/>
        Save
    </button>    <a href="/password/reset/">
        <img src="/images/icons/textfield_key.png" alt=""/>
        Change Password
    </a>    <a href="#" class="negative">
        <img src="/images/icons/cross.png" alt=""/>
        Cancel
    </a>
</div>
```
_Tip_: Always specify the type attribute for a button element. Different browsers use different default types for the button element.

## 3.2 Styles and Sizes (With Bootstrap)

Great Work! As we know, this is where we would start using only CSS to style and size our buttons..? No! We are introducing you to Bootstrap (the most popular HTML, CSS, and JavaScript framework for developing responsive, mobile-first web sites) because it´s an easier way to get the job done!

### [](https://github.com/dwyl/learn-html5#do-you-prefer-larger-or-smaller-buttons)Do you prefer larger or smaller buttons?

Add .btn-lg (large), .btn-md(medium), .btn-sm(small), or .btn-xs(extra-small) for additional sizes.
```html
<button type="button" class="btn btn-primary btn-lg">Large</button>
<button type="button" class="btn btn-primary btn-md">Medium</button>
<button type="button" class="btn btn-primary btn-sm">Small</button>
<button type="button" class="btn btn-primary btn-xs">XSmall</button>
```
Create block level buttons — those that span the full width of a parent—by adding _.btn-block_:
```html
<button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button>
```
After you decide the size of your buttons it´s time to style them! Bootstrap provides different styles of buttons:

-   Basic
-   Default
-   Primary
-   Success
-   Info
-   Warning
-   Danger
-   Link
```html
<!-- Provides extra visual weight and identifies the primary action in a set of buttons -->
<button type="button" class="btn btn-primary">Primary</button>
<!-- Secondary, outline button -->
<button type="button" class="btn btn-secondary">Secondary</button>
<!-- Indicates a successful or positive action -->
<button type="button" class="btn btn-success">Success</button>
<!-- Contextual button for informational alert messages -->
<button type="button" class="btn btn-info">Info</button>
<!-- Indicates caution should be taken with this action -->
<button type="button" class="btn btn-warning">Warning</button>
<!-- Indicates a dangerous or potentially negative action -->
<button type="button" class="btn btn-danger">Danger</button>
<!-- Deemphasize a button by making it look like a link while maintaining button behavior -->
<button type="button" class="btn btn-link">Link</button>
```
### [](https://github.com/dwyl/learn-html5#outline-buttons)Outline buttons

Replace the default modifier classes with the _.btn-outline-_ ones to remove all background images and colors on any button.
```html
<button type="button" class="btn btn-outline-primary">Primary</button>
<button type="button" class="btn btn-outline-secondary">Secondary</button>
<button type="button" class="btn btn-outline-success">Success</button>
<button type="button" class="btn btn-outline-info">Info</button>
<button type="button" class="btn btn-outline-warning">Warning</button>
<button type="button" class="btn btn-outline-danger">Danger</button>
```

### Great resources to learn HTML5

[https://developer.mozilla.org/en-US/docs/Web/HTML/Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

## 4.1 [[CSS]]
