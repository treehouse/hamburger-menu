# hamburger-menu

Hamburger menus are great for toggling a mobile navigation. Adding slick animations to show the open or closed state can be tricky but I will explain how this can be done pretty easily. Let's get started. 😎

We'll need to create a few files; `index.html`, `styles.css`, & `app.js`. 


## HTML

In our `index.html` file, let's setup a navigation with `<nav></nav>`.

Inside our nav tag, we'll create a container for our hamburger menu. This will just be a div with the class of hamburger-menu.

```
<nav>
    <div class="hamburger-menu"></div>
</nav>
```

Next, we'll add in each of the three hamburger menu 'bars'. These will be divs with the class of 'ham-bar' but they will each get a unique class name as well. This is the code I'll be working with:

```
<nav>
    <div class="hamburger-menu">
        <div class="ham-bar bar-top"></div>
        <div class="ham-bar bar-mid"></div>
        <div class="ham-bar bar-bottom"></div>
    </div>
</nav>
```

That should be it for our HTML, so now let's tackle the CSS.

## CSS

We can get started with some basic styles and resets:

```
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #ccc;
}
```