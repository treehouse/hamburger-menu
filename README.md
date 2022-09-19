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

Once that's done, lets add some quick stylings to the nav.

```
nav {
    padding: 1rem;
    background-color: #222;

    display: flex;
    justify-content: flex-end;
    align-items: center;
}
```

Since the only child element of our nav is the `<div class="hamburger-menu"></div>` we can use `flex` to justify the content to `flex-end` so that our hamburger menu is all the way to the right.

Next, we can start styling our actual hamburger menu.

```
.hamburger-menu {
    height: 50px;
    width: 50px;
    position: relative;
    cursor: pointer;
    padding: 1rem;
}
```

We position this `relative` since its child elements (`<div class="ham-bar"></div>` * 3) will need to be positioned absolutely.

All of the `<div class="ham-bar"></div>` elements will get the following styles:

```
.ham-bar {
    width: 70%;
    height: 4px;
    background-color: white;
    border-radius: 25px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    transition: transform .6s, opacity .8s, top .6s;
}
```

You'll notice you can only see one `ham-bar` now. Actually, all three are visible. They're just all absolutely positioned to the center of `.hamburger-menu`. So let's adjust the `bar-top` and `bar-bottom`:

```
.bar-top {
    top: 25%;
}

.bar-bottom {
    top: 75%;
}
```

Now you should see your hamburger menu! Next, we'll want to hop into the HTML and add a class of `active` to our `<div class="hamburger-menu"></div>`. This is because when we click on our hamburger menu, we'll want to toggle this class on and off. 

When the hamburger menu has a class of `active`, we'll want to style the `<div class="ham-bar"></div>` appropriately. Lets do that now.

For `bar-top` we want to center it and rotate it:
```
.hamburger-menu.active .bar-top {
    transform: translate(-50%, -50%) rotate(-315deg);
    top: 50%;
}
```

for `bar-mid` we want to set the opacity to 0:
```
.hamburger-menu.active .bar-mid {
    opacity: 0;
}
```

for `bar-bottom` we want to center it and rotate it:
```
.hamburger-menu.active .bar-bottom {
    transform: translate(-50%, -50%) rotate(-225deg);
    top: 50%;
}
```

Now go ahead and add a class of `active` to your hamburger-menu in the HTML to make sure your hamburger-menu resembles and 'x'. If it does, great! If not, make sure to re-read the above and figure out where you've gone wrong. Once that's done, let's move on to toggling this `active` class via JavaScript!

## JavaScript

The JavaScript is very simple, we'll just want to add an event listener on `<div class="hamburger-menu"></div>`. We can create a variable for this as well:
```
const hamMenu = document.querySelector('.hamburger-menu');
hamMenu.addEventListener('click', () => {

});
```

All we want to do when this event is triggered, is toggle a class of `active` to `<div class="hamburger-menu"></div>`:
```
const hamMenu = document.querySelector('.hamburger-menu');
hamMenu.addEventListener('click', () => {
    hamMenu.classList.toggle('active');
});
```

And that's it, your hamburger menu should toggle both the open and closed state when clicked! 