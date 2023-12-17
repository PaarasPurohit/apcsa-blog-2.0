---
comments: True
layout: notebook
title: Teaching Hacks
description: Hacks completed for Tri 2 lessons
type: tangibles
toc: True
courses: {'csa': {'week': 14}}
categories: ['C4.1']
permalink: /teaching-hacks
---

## Unit 1: SASS Fundamentals

Hack Question: Can you guess what its changing style of the text to? 

```css
body {
    color: #0000FF;
    font-family: Ariel, sans-serif;
    font-size: 16px;
}
```

**Nesting**

> What is nesting? 
    > Answer here (hack question): 
- Nesting is a way to organize your code and make it easier to read. It also helps keep your code <u>DRY (Don't Repeat Yourself)</u> . 
- Nesting is when you put one selector inside another selector. This is a great way to keep your code organized and make it easier to <u>read</u>. 
- When we make HTML we often nest different <u>elements</u> within each other and have a clear structure when we look at it.
- The problem is that in regular CSS we don't have that so we need to use SASS to help us organize our code.

- Warning: Don't nest too much as when the CSS is processed it can make overqualified selectors which can be hard to read and maintain. Which means that it would only target that specific element type and not any other elements that have the same class name.

**Sass Nesting**
- Through nesting the ul, li, and a selectors within the nav selector makes your CSS better and increases its readability overall.

**Variables**
> What is a variable?
- A variable is a container that stores <u>information</u> so for instance when you have multiple places that refer to one value you can just use the variable name instead of the value.
- This is valuable in SASS because it allows you to reuse that <u>value</u> in multiple places throughout your stylesheet. 
- The $ symbol is used in Sass to designate a variable. 

Pro Tip: The reason SASS variables are better than variables in regular CSS is that they are easier to read with a much simpler syntax. 

Fun Fact: Variables in SASS came before CSS and often SASS has features long before they are actually added to CSS as a whole. 

**Variable Example Syntax**
- $variable-name: value;
- Once the sass is processed the variable name is replaced with the value throughout the program.

**Mixins**: What is a mix in what are we mixing in? Answer here (hack question): 

> A mixin is kind of a class. If you're taking the name "mixin" at face value, we're "mixing in" different styles that other elements can include.

**Inheritance**
> What is inheritance? Answer here (hack question): 

- In general programming concept where the child class can <u>inherit</u> properties from the <u>parent</u> class. These properties can be changed and modified in the <u>child</u> class. This prevents code from being repeated and makes the code more usable and flexible.
- In SASS we have a similar concept that can be used as well we can create base styles and then have other styles inherit from them and then we can change them as we please. 
- We can do that by through using @extend .name-of-class and then we can add more styles to it as we please. Simple as that.

**SASS Demo**:

Below is the SASS code I used:

```scss
  // Variables
  $primary-color: #3498db;
  $secondary-color: #2ecc71;
  $card-background: #ecf0f1;
  $card-hover: #bdc3c7;

  // Mixins
  @mixin transition($property: all, $duration: 0.3s, $timing-function: ease-in-out) {
    transition: $property $duration $timing-function;
  }

  // Styles
  .card {
    background-color: $card-background;
    border-radius: 8px;
    padding: 20px;
    margin: 20px;
    width: 300px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

    // Nesting and hover effect
    &:hover {
      background-color: $card-hover;
    }

    // Title styling
    h2 {
      color: $primary-color;
      margin-bottom: 10px;
    }

    // Content styling
    p {
      color: $secondary-color;
    }

    // Apply transition mixin
    @include transition(background-color);
  }

  // Usage example
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  // Create multiple cards with different colors
  .card-one {
    @extend .card;
    $card-background: #e74c3c;
    $card-hover: #c0392b;
  }

  .card-two {
    @extend .card;
    $card-background: #f39c12;
    $card-hover: #d35400;
  }

  .card-three {
    @extend .card;
    $card-background: #2c3e50;
    $card-hover: #34495e;

    h2 {
      color: #e74c3c; // Customize title color for this card
    }

    p {
      color: #f39c12; // Customize content color for this card
    }
  }
```

And here is the [running project](https://nvarap.github.io/CSA_Tri2_Project1/sass-ui-demo)

## Unit 2: UX/UI Through JQuery & CRUD

**What is UX?**
- UX is the shortform of <u>user experience</u>; a standard of understanding the <u>usability</u> of a product and optimise it based on data recived from users.

- UX is a <u>necessity</u> in all industries since collecting UX and improving the product based on it increases the <u>popularity</u> of the product on the market, increasing profits of the company or collaboration.

**What is jQuery?**

- **jQuery** is a lightweight, "<u>write less, do more</u>”, JavaScript library. The purpose of jQuery is to make it much easier to use JavaScript on your site and it simplifies many tasks that require many lines of JavaScript code to accomplish, wraping them into <u>methods</u> that you can call with a single line of code.

- **jQuery** also simplifies a lot of the complicated things from JavaScript, like AJAX calls and DOM manipulation.

- With jQuery you select (query) HTML elements and perform "<u>actions</u>" on them.

- All jQuery methods begin inside a document <u>ready</u> event

**Popcorn Hack: Name 3 other event HTML events**

1. hover
2. onpress
3. onreload

**What Does CRUD Stand For?**
- Answer this as a Popcorn Hack: <u>Create, Read, Update, Delete</u>

**Popcorn Hack: Complete the Jquery and JavaScript code**: This represents a website for buying dogs. The API contains an id, name, price, and breed for each dog. Display them all as html using jQuery.

```html
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <style>
        .dog {
            border: 1px solid #ddd;
            margin-bottom: 20px;
            padding: 20px;
            border-radius: 5px;
        }
        .price {
            color: #007BFF;
        }
    </style>
</head>
<body>

<div id="dogs"></div>

<script>
// Fake API function
function getAPI() {
    return [
        {id: 1, name: 'Max', price: '$1000', breed: 'Golden Retriever'},
        {id: 2, name: 'Bella', price: '$800', breed: 'Labrador Retriever'},
        {id: 3, name: 'Charlie', price: '$1200', breed: 'German Shepherd'}
    ];
}

$(document).ready(function(){
    var dogs = getAPI();
    $.each(dogs, function(i, dog) {
        var dogHtml = '<div class="dog"><h2>Dog ' + dog.id + '</h2><p>Name: ' + dog.name + '</p><p>Breed: ' + dog.breed + '</p><p class="price">Price: ' + dog.price + '</p></div>';
        $('#dogs').append(dogHtml);
    });
});
</script>
</body>
```

In the following example, write in one of the comments where the selector is (popcorn hack ~ raise hand when found)


```java
$(document).ready(function(){     // 
    $("button").click(function(){ // Selector
      $("p").hide();              // Selector
    });                           //
  });                             //
```

<html>
<head>
    <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        #app {
            max-width: 400px;
            width: 100%;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            padding: 20px;
            border-radius: 8px;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 8px;
            border-bottom: 1px solid #ddd;
        }
        button {
            cursor: pointer;
        }
        .completed {
            text-decoration: line-through;
            color: #888;
        }
    </style>
</head>
<body>

<div id="app">
    <h1>Todo List</h1>
    <input type="text" id="newItem" placeholder="Add new item">
    <button id="addItem">Add</button>
    <ul id="todoList"></ul>
</div>

<script>
$(document).ready(function(){
    // Initial data
    var todoList = [
        {id: 1, text: 'Task 1', completed: false},
        {id: 2, text: 'Task 2', completed: true},
        {id: 3, text: 'Task 3', completed: false}
    ];

    // Function to render the todo list
    function renderTodoList() {
        $('#todoList').empty();
        $.each(todoList, function(index, item) {
            var listItem = $('<li>').attr('data-id', item.id).toggleClass('completed', item.completed).append(
                $('<span>').text(item.text),
                $('<button>').text('Edit').click(function() {
                    var newText = prompt('Edit item:', item.text);
                    if (newText !== null) {
                        item.text = newText;
                        renderTodoList();
                    }
                }),
                $('<button>').text('Delete').click(function() {
                    todoList = todoList.filter(function(todoItem) {
                        return todoItem.id !== item.id;
                    });
                    renderTodoList();
                }),
                $('<button>').text('Check').click(function() {
                    item.completed = !item.completed;
                    renderTodoList();
                })
            );
            $('#todoList').append(listItem);
        });
    }

    // Initial rendering
    renderTodoList();

    // Add new item
    $('#addItem').click(function() {
        var newItemText = $('#newItem').val();
        if (newItemText.trim() !== '') {
            var newItem = {
                id: todoList.length + 1,
                text: newItemText,
                completed: false
            };
            todoList.push(newItem);
            renderTodoList();
            $('#newItem').val('');
        }
    });
});
</script>

</body>
</html>

This program includes a simple Todo list with CRUD functionality, and you can check/uncheck items. It has a clean and responsive design, making use of flexbox for layout. The extra feature is the "Check" button that toggles the completion status of each item.

**All Hacks Done**
