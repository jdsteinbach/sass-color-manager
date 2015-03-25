# SCM: Sass Color Manager

A small Sass library for managing colors and their variations throughout a project

## What SCM does

Everything SCM does is based on two maps: one for colors and one for variants. It provides a function to get any color in any pre-set variant:

```
.element {
  color: scm(red, dark);
}
```

## How to add colors

To add a color, use the `scm-add-color()` mixin. It needs two arguments: a label for the color and its hex value:

```
@include scm-add-color(brand-blue, #205D84);
```

## How to add variants

To add a variant, use the `scm-add-variant()` mixin. It takes three arguments: a label for the variant, the name of the [Sass color function](http://sass-lang.com/documentation/Sass/Script/Functions.html#rgb_functions) it uses, and the parameters for that function:

```
@include scm-add-variant(fade, rgba, .7);
@include scm-add-variant(dark, darken, 10%);
@include scm-add-variant(blueish, mix, (blue, 10%));
```

## How to use the colors

In your Sass, use the function `scm(color, variant)` anywhere you can put a CSS color:

```
.test {
  color: scm(red, dark);
  border: 3px solid scm(orange, fade);
  
  &:hover {
    color: scm(red);
    border-color: scm(orange, light);
  }
}
```