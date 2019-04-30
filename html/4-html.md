# Wireframing & Basic Flexbox

## Sequence

1. [Wireframing](#wireframing)
2. [Flexbox Parents And Children](#flexbox)
3. [Properties for the Parent](#properties-for-the-parent)
4. [Properties for the Child Elements](#properties-for-the-child-elements)

## Wireframing

A wireframe is a visual representation or sketch of a webpage. Why would it be important to know what you want your website to look like before you start coding it? This may seem obvious, but you'd be amazed at how many first-time developers just jump in and start throwing code on an html file.

Here's an [example](https://wireframe.cc/oQEVPW). We'll use this for our code-along. Ask students what they notice.
> It's sparse. The actual text isn't written. The images are just giant rectangles. There are three rows.

Have students wireframe their ideal reorganization of their profile page.

Clarify that this will be the goal by the END of the session, but before we get there, we need to learn how to create flexbox containers.

## Flexbox

A Flexbox layout is made of parent elements which we can call containers or rows, and child elements, which we could call items or columns.

Below is the sample code for this lesson. You can disseminate the code via Slack, or a cloning mechanism like GitHub or Glitch.

Have students examine the body of this HTML document, and identify how many parent elements there are (3) and how many child elements there are (10).

### Starter HTML code
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Test Page</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="row" id="row1">
      <div class="item" id="ruby">Ruby</div>
      <div class="item" id="python">Python</div>
    </div>
    <div class="row" id="row2">
      <div class="item" id="p5">p5.js</div>
      <div class="item" id="bootstrap">Bootstrap</div>
      <div class="item" id="js">JavaScript</div>
    </div>
    <div class="row" id="row3">
      <div class="item" id="swift">Swift</div>
      <div class="item" id="hyper">HTML</div>
      <div class="item" id="aframe">A-Frame</div>
      <div class="item" id="css">CSS</div>
      <div class="item" id="java">Java</div>
    </div>
  </body>
</html>
```

### Starter CSS code
```css
/* The first chunk of this style exist primarily so that you can see the elements - Flexbox would work without it, but it's easier to see when the font is large and the items have a background color */
/* Border-box sizing */
*, *:before, *:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

/* Default to a sans-serif font */
html {
  font-family: sans-serif;
}

/* Make the fonts text large, white, and spacious */
.item {
  font-size: 32px;
  color: white;
  text-shadow: 3px 3px rgba(0, 0, 0, 0.4);
  font-weight: 900;
  text-align: center;
  white-space: nowrap;
  padding: 12px 4px;
  margin-bottom: 0;
  margin-top: 0;
}

/* Make rows visible */
.row {
  min-height: 100px;
  margin: 10px;
  background-color: rgba(0, 0, 0, 0.1);
}

/* Color each language element */
#ruby {background-color: #DF4638;}
#python {background-color: #8DAD53;}
#js {background-color: #A8D3DD;}
#hyper {background-color: #F7CC77;}
#css {background-color: #2454DB;}
#aframe {background-color: #DB4260;}
#p5 {background-color: #E88A9F;}
#bootstrap {background-color: #7157AD;}
#java {background-color: #CA2B1D;}
#swift {background-color: #ED7B46;}

/* ----------------------------------------------- */
/* ---Please do not modify code above this line--- */
/* ----------Code your flex classes below--------- */
/* ----------------------------------------------- */

/* Parent or Container elements */
/* Style them all at once with this selector */
.row {

}

/* OR Style each row individually with these selectors */
#row1 {

}

#row2 {

}

#row3 {

}

/* Child elements or items */
.item {

}
```

Note that in order for the css to render properly, it will need to be placed inside an adjacent file named `style.css`.

## Flexbox

### Parent and Child: Basic flex setup

The divs with a class of `.row` will be acting as rows; they will be **parent** elements. The divs with a class of `.item` will be contained *inside* the rows, so they'll become **child** elements.

The most critical pieces of information for the **parent** elements has to do with how it will display its contents. We'll give it the css property `display: flex;`. This means the items inside it will have some amount of flexibility in terms of their size.

**Preview the page. Probe for what happened when the parents are set to `display: flex`.**

## Properties for the parent

Most of the most powerful aspects of flexbox come into play when we apply one or more styling properties to the parent element. While child elements can be styled individually to display differently from their peers, that behavior is useful less frequently than the following properties for the parent:
* flex-direction
* align-items
* justify-content

### Flex Direction

When we added `display: flex;` to our `.row` ruleset, the three parent elements became rows. But flexbox containers can display in any of four directions:
* `row`
* `column`  
* `row-reverse`
* `column-reverse`

With students, try out the following properties. Do this one at a time, and preview the results each time so that students isolate their understanding of what each new property is doing.

```css
/* Parent or Container elements */
/* Style them all at once with this selector */
.row {
  display: flex;
}

/* OR Style each row individually with these selectors */
#row1 {
  flex-direction: row-reverse;
}

#row2 {
  flex-direction: column;
}

#row3 {
  flex-direction: row;
}
```

It's worth noting that `row-reverse` is subtle, and `row` is the default behavior, so breaking them down and previewing one at a time gives students more time to focus on these behaviors. Students will to struggle to understand why `flex-direction: row` would be useful if it's already the default behavior - ask for theories, but refrain from giving any prescriptive answers.

Once students have mastered the `flex-direction` property, remove the property from all three rows before exploring the next property.

### Align Items

Align items is a very useful property that determines how the content of a parent element are situated within that container. The four values you're most likely to see associated with this property are `stretch`, `flex-start`, `flex-end`, and `center`.

The value `stretch` is the default, and based on their observations, students might already be able to surmise as much, so ask a few check for understanding questions or demo with a prediction, and then experiment with the other three values.

As before, make one change at a time, and preview after each change so as to isolate the noticeable changes.

```css
#row1 {
  align-items: flex-start;
}

#row2 {
  align-items: flex-end;
}

#row3 {
  align-items: center;
}
```

Name for students that the `align-items` property can be used in combination with other properties like `flex-direction`, but to eliminate possibly confusing interactions while we're just learning, clear out the contents of these rulesets before moving on.

Note that the `min-height` property used in the starter code is going to make all of these `align-items` properties more noticeable, but also less aesthetically pleasing. Feel free to remove the minimum height after this, as it's less necessary for the `justify-content` property.

### Justify Content

The most commonly used and powerful flex property for the parent is the `justify-content` property. The values you'll see most often associated to it can be broken up into two categories:

Values that cluster child elements together:
* `flex-start`
* `flex-end`
* `center`

Values that space child elements apart:
* `space-between`
* `space-around`
* `space-evenly`

As before, explore these changes one at a time with students, and solicit predictions before each preview.
```css
#row1 {
  justify-content: flex-start;
}

#row2 {
  justify-content: flex-end;
}

#row3 {
  justify-content: center;
}
```

After you feel you've mastered those three properties, explore the other three values. Once again, do these one at a time.
```css
#row1 {
  justify-content: space-between;
}

#row2 {
  justify-content: space-around;
}

#row3 {
  justify-content: space-evenly;
}
```

### Major & Minor Axes

One of the most common misconceptions about the properties listed here is that `align-items` controls vertical space and positioning, and `justify-content` controls horizontal space and conditioning. That's only true when the flex direction is set to `row` or `row-reverse`.

When the `flex-direction` is set to `column` or `column-reverse`, **those properties switch**: `align-items` controls *horizontal* space and positioning, and `justify-content` controls *vertical* space and conditioning.

If you need a consistent way to remember this, the unifying factor is that `justify-content` controls the positioning ALONG the `flex-direction`, and  `align-items` controls the positioning PERPENDICULAR to the `flex-direction`.

With that said, even experienced developers frequently refer back to the [Flexbox Cheat Sheet](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) all the time, so instead of putting any effort into rote memorization, bookmark that page and refer back to it often.

## Properties for the Child Elements

There are a lot of properties for child elements, but most of them operate directly in opposition to the parent properties.

One very useful property, `flex`, allows child elements to size themselves to take up all the room within the parent container.

There are three behaviors you're most likely see implemented are:
* `flex: 0;` - Child elements will not expand or contract. They will stay the exact size specified by your css (default behavior).
* `flex: 1;` - Child elements will expand or contract to take up exactly all the available space in the parent element, sizing themselves equally to all their siblings.
* `flex: auto;` - Child elements will expand or contract to take up exactly all the available space in the parent element, sizing themselves proportionally to their content (elements with more text will take up more space).

Try this one in context:
```css
* Parent or Container elements */
/* Style them all at once with this selector */
.row {
  display: flex;
}

/* OR Style each row individually with these selectors */
#row1 {

}

#row2 {

}

#row3 {

}

/* Child elements or items */
.item {
  flex: 1;
}
```

It's worth noting that this discussion / explanation of the `flex: 1;` property is very abbreviated, and is usually more complex than is productive for student exploration at this time. For more detail, go to the [Flexbox Cheat Sheet](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), and encourage students who are curious to do the same.

## Applications

Now that we understand how the items work in isolation, here are some mini-challenges you can go through with students.

1. Squish all the content in alternating directions.
2. Center all the content in each row.
3. Make the middle row a column, and center the contents within the column.
4. Make all three rows into columns at least 400px tall, and have their contents flex to take up all the space inside.
5. STRETCH: Display all three columns next to each other (kind of like Pinterest).
