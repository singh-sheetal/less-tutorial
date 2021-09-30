What is Less?

Less is a preprocessor that adds more to the functionality of the CSS.

Variables:

Example:
```html
<div class="header">Header</div>
```

```css
@width: 20px;
@height: @width;
.header {
    width: @width;
    height: @height;
}
```
Example:
```html
<div class="image"></div>
```

```css
@images: "../images";
.image {
    background: url("@{images}/download.png");
}
```
Example:
```html
<div class="header">Header</div>
```

```css
.header {
  color: #efefef;
  background-color: $color;
}
```

Example:
```html
<div class="header">Header</div>
```

```css
.header {
  color: #efefef;
  background-color: $color;
  color: red;
}
```

Scope in variables:
Variables and mixins are first looked for locally, and if they aren't found, it's inherited from the "parent" scope.

Example:
```html
    <div class="header">Header</div>
```

```css
@var: red;
  .header {
    @var: white;
    color: @var; // white
  }
```

Parent Selectors:
The & operator represents is most commonly used when applying a modifying class or pseudo-class to an existing selector.

Example:
```html
<a class="link"></a>
```

```css
a {
  color: blue;
  &:hover {
    color: green;
  }
}

OR

.link {
  color: blue;
  &:hover {
    color: green;
  }
}
```

Example:
```html
    <div class="parent">
        Parent
        <div class="parent-child">Child</div>
    </div>
```

```css
.parent {
    border: 1px solid black;
    &-child {
        border: 1px solid @red;
    }
}
```

Mixins:
"mix-in" properties from existing styles.

Example:
```html
<div class="header">Header</div>
```

```css
#colors() {
    bg-color: yellow;
    text-color: red;
}
.a, #b {
  color: red;
}
.header {
    color: #colors[text-color];
}
```
Mixins created with parentheses will not be included in the generated CSS file.

Selectors in mixins
Example:
```html
<div class="header">Header</div>
```

```css
#hover-mixin {
    &:hover {
        background: yellow;
    }
}
.header {
    #hover-mixin();
}
```

Namespaces
Namespaces are used to include multiple classes/ids inside a mixin

Example:
```html
<div class="header">Header</div>
```

```css
#bundle() {
    .red-color {
        background: red;
    }
  }
.header {
    #bundle.red-color();
}
```

Parametric Mixins
Mixins can also take arguments, which are variables passed to the block of selectors when it is mixed in.
Example:
```html
<div class="header">Header</div>
```

```css
.border-radius(@radius) {
  -webkit-border-radius: @radius;
     -moz-border-radius: @radius;
          border-radius: @radius;
}

.header {
    .border-radius(4px);
}
```

Overloading Mixins
Multiple mixins with the same name and number of parameters.

Example:
```html
<div class="header">Header</div>
```

```css
.mixin(@color) {
  color: @color;
}
.mixin(@color, @padding: 2) {
  color: @color;
  padding: @padding;
}

.header {
    .mixin(red);
}
```

Media Queries:
Media queries are useful when you want to modify your site or app depending on a device's general type (such as print vs. screen) or specific characteristics and parameters (such as screen resolution or browser viewport width).

Example:
```html
<div class="header">Header</div>
```

```css
.header {
    color: red;
    @media screen and (max-width: 1920px) { 
        color: purple;
    }
}
```


