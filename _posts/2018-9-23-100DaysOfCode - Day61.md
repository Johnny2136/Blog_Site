---
layout: post
title: Day 61 of 100 Days Of Code
---

![Sunday](https://discourse-user-assets.s3.amazonaws.com/original/3X/1/3/13f966666ac2e06ae8cd3f7cfda01641494e0946.png)

## Day 61: September 23, Sunday

**Today 's Progress**: Started lessons on [Introduction to the Data Visualization with D3 Challenges](https://learn.freecodecamp.org/data-visualization/data-visualization-with-d3).

**Thoughts**: Started the D3.js lessons and Challenges, I feel there is some content missing from `#freeCodeCamp` On a positive note so far most of examples are pretty good.

### Resources used:
  * [JSFiddle](https://jsfiddle.net/johnny2136/1pLubnqc/)
  * [REPL.IT](https://repl.it/@JohnJohnson2/FCCD3)
  * [GitHub_FCC_Repo](https://github.com/Johnny2136/FCC-Projects/blob/master/FCC_Challenges/DataVisualizationWithD3.md)
  * [Binding Data to DOM Elements](https://www.dashingd3js.com/binding-data-to-dom-elements)
  * [D3 Tutorial](https://www.dashingd3js.com/table-of-contents)
  * [D3 in Depth](https://d3indepth.com/)

 ### Add Document Elements with D3

  **The Lesson:**
  D3 has several methods that let you add and change elements in your document.

  The `select()` method selects one element from the document. It takes an argument for the name of the element you want and returns an HTML node for the first element in the document that matches the name. Here's an example:

  `const anchor = d3.select("a");`

  The above example finds the first anchor tag on the page and saves an HTML node for it in the variable anchor. You can use the selection with other methods. The "d3" part of the example is a reference to the D3 object, which is how you access D3 methods.

  Two other useful methods are `append()` and `text()`.

  The `append()` method takes an argument for the element you want to add to the document. It appends an HTML node to a selected item, and returns a handle to that node.

  The `text()` method either sets the text of the selected node, or gets the current text. To set the value, you pass a string as an argument inside the parentheses of the method.

  **Example:**
  Here's an example that selects an unordered list, appends a list item, and adds text:
  ```JavaScript
  d3.select("ul")
    .append("li")
    .text("Very important item");
  ```
  D3 allows you to chain several methods together with periods to perform a number of actions in a row.

  **Challange Instructions:**
  Use the select method to select the `body` tag in the document. Then append an `h1` tag to it, and add the text "Learning D3" into the `h1` element.

  **MySolution**
  ```JavaScript
  <body>
    <script>
      // Add your code below this line
      d3.select("body")
        .append("h1")
        .text("Learning D3");    
      // Add your code above this line
    </script>
  </body>
  ```


  ### Select a Group of Elements with D3

  **The Lesson:**
  D3 also has the `selectAll()` method to select a group of elements. It returns an array of HTML nodes for all the items in the document that match the input string. Here's an example to select all the anchor tags in a document:

  **Example:**
  `const anchors = d3.selectAll("a");`

  Like the `select()` method, `selectAll()` supports method chaining, and you can use it with other methods.

  **Challange Instructions:**
  Select all of the `li` tags in the document, and change their text to "list item" by chaining the `.text()` method.

  *notes:* I would have made the following example:

  ```JavaScript
  <body>
    <a href="">Example</a>
    <a href="">Example</a>
    <a href="">Example</a>
    <script>
       const anchors = d3.selectAll("a")
        .test("SomeURL");     
    </script>
  </body>
  ```
  *Resources:* https://d3indepth.com/selections/

  **My solution**
  ```JavaScript
  <body>
    <ul>
      <li>Example</li>
      <li>Example</li>
      <li>Example</li>
    </ul>
    <script>
      // Add your code below this line
      const anchors = d3.selectAll("li")
        .text("list item");     
      // Add your code above this line
    </script>
  </body>
  ```


  ### Work with Data in D3

  **The Lesson:**
  The D3 library focuses on a data-driven approach. When you have a set of data, you can apply D3 methods to display it on the page. Data comes in many formats, but this challenge uses a simple array of numbers.

  The first step is to make D3 aware of the data. The `data()` method is used on a selection of DOM elements to attach the data to those elements. The data set is passed as an argument to the method.

  A common workflow pattern is to create a new element in the document for each piece of data in the set. D3 has the `enter()` method for this purpose.

  When `enter()` is combined with the `data()` method, it looks at the selected elements from the page and compares them to the number of data items in the set. If there are fewer elements than data items, it creates the missing elements.

  **Example:**
  Here is an example that selects a ul element and creates a new list item based on the number of entries in the array:
  ```html
  <body>
    <ul></ul>
    <script>
      const dataset = ["a", "b", "c"];
      d3.select("ul").selectAll("li")
        .data(dataset)
        .enter()
        .append("li")
        .text("New item");
    </script>
  </body>
  ```
  It may seem confusing to select elements that don't exist yet. This code is telling D3 to first `select` the `ul` on the page. Next, `select all` list items, which returns an empty selection. Then the `data()` method reviews the dataset and runs the following code three times, once for each item in the array. The `enter()` method sees there are no `li` elements on the page, but it needs 3 (one for each piece of data in dataset). New `li` elements are appended to the `ul` and have the text "New item".

  **Challange Instructions:**
  Select the `body` node, then select all `h2` elements. Have D3 create and `append` an `h2` tag for each item in the dataset array. The text in the `h2` should say "New Title". Your code should use the `data()` and `enter()` methods.

  *Resources:* https://www.dashingd3js.com/binding-data-to-dom-elements

  **My solution**
  ```JavaScript
  <body>
    <script>
      const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];

      // Add your code below this line
      d3.select("body").selectAll("h2")
        .data(dataset)
        .enter()
        .append("h2")
        .text("New Title #3");   
      // Add your code above this line
    </script>
  </body>
  ```


  ### Work with Dynamic Data in D3

  **The Lesson:**
  The last two challenges cover the basics of displaying data dynamically with D3 using the `data()` and `enter()` methods. These methods take a data set and, together with the `append()` method, create a new DOM element for each entry in the data set.

  In the previous challenge, you created a new `h2` element for each item in the dataset array, but they all contained the same text, "New Title". This is because you have not made use of the data that is bound to each of the `h2` elements.
  **Example:**
  The D3 `text()` method can take a string or a callback function as an argument:

  `selection.text((d) => d)` adding `d + 'text');` Would have been helpfull???

  In the example above, the parameter d refers to a single entry in the dataset that a selection is bound to.

  Using the current example as context, the first `h2` element is bound to 12, the second `h2` element is bound to 31, the third `h2` element is bound to 22, and so on.

  **Challange Instructions:**
  Change the `text()` method so that each `h2` element displays the corresponding value from the dataset array with a single space and "USD". For example, the first heading should be "12 USD".

  *Resources:* https://forum.freecodecamp.org/t/work-with-dynamic-data-in-d3-help/222552/4

  **My solution**
  ```JavaScript
  <body>
    <script>    
      const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];        
        d3.select("body").selectAll("h2")
        .data(dataset)
        .enter()
        .append("h2")
        // Add your code below this line      
        .text((d) => d + ' USD');      
        // Add your code above this line    
    </script>
  </body>
  ```


  ### Add Inline Styling to Elements

  **The Lesson:**
  D3 lets you add inline CSS styles on dynamic elements with the style() method.

  The style() method takes a comma-separated key-value pair as an argument.

  **Example:**
  Here's an example to set the selection's text color to blue:

  `selection.style("color","blue");`

  **Challange Instructions:**
  Add the style() method to the code in the editor to make all the displayed text have a font-family of verdana.

  *Resources:* Easy one...

  **My solution**
  ```JavaScript
  <body>
    <script>
      const dataset = [12, 31, 22, 17, 25, 18, 29, 14, 9];    
      d3.select("body").selectAll("h2")
        .data(dataset)
        .enter()
        .append("h2")
        .text((d) => (d + " USD"))
        // Add your code below this line
        .style("font-family","verdana");      
        // Add your code above this line
    </script>
  </body>
  ```

**Link(s) to work**

1. Started work on [Introduction to the Data Visualization with D3 Challenges](https://learn.freecodecamp.org/data-visualization/data-visualization-with-d3).

**Introduction to the Data Visualization with D3 Challenges**

 - [x] Add Document Elements with D3
 - [x] Select a Group of Elements with D3
 - [x] Work with Data in D3
 - [x] Work with Dynamic Data in D3
 - [x] Add Inline Styling to Elements

All code is in GitHub [FCC_Challenges/DataVisualizationWithD3.md](https://github.com/Johnny2136/FCC-Projects/edit/master/FCC_Challenges/DataVisualizationWithD3.md).
