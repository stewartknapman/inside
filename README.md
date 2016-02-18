# Inside SCSS

### A sassy skeleton framework

[Inside is a sass based skeleton framework](http://stewartknapman.github.io/inside/). It aims to set up some basic ground-rules and then get out of the way. That way you can then apply your own styles on top.

Everything is based on mixins so that you can keep your sass light, but you can include all the classes if you need to get something up and running quickly.

Each modules set of classes can also be turned on and off through variables so you don't have to include things that you don't need, keeping everything light and manageable.

## Getting setup

**Step1:** Install Inside into your project via npm

``` 
npm install inside-scss
```

**Step2:** Include Inside in your projects main scss file.

``` scss
...
@import 'node_modules/inside-scss/src/inside';
...
```

This path is reletive to where your main scss file is stored within your project, so if your file is within `src/scss/styles.scss` then the path to inside will look like this: `'../../node_modules/inside-scss/src/inside'`

**Step 3:** Profit!

## Globals & Modules

### Classes

Everything in Inside is a mixin. This way it can be as light and modualr as you need, however each mixin has its own class for convenience.

For example to add the base button styles you can use the `button-base` mixin:

``` 
.my-button-class {
  @include button-base;
}
```

Or for convenience you can just use the class `.button` directly in your markup.

**All classes are included by default** which means that they will be included in your css when the scss files are compiled.

But if you don't want all of these classes creating bloat in your css and you are just using the mixins directly then you can set the `$include_classes` variable to be false.

### Modules

You can also turn off the classes for each module individually. This is good if you find you are not using a particular module and thus don't need its classes.

So far these modules are:

``` scss
$include_grid:    true !default;
$include_type:    true !default;
$include_lists:   true !default;
$include_forms:   true !default;
$include_buttons: true !default;
$include_tables:  true !default;
$include_hero:    true !default;
$include_code:    true !default;
$include_embed:   true !default;
```

### Opinions

I'm pretty opinionated about how I build sites and have included a few of those opinions here in Inside. But if you don't like my opinions you can opt-out by setting the associated variable to false.

If you really *REALLY* don't like my opinions you can ~~find~~ [fight me](https://m.popkey.co/f741ba/gKJOZ.gif) on [twitter](https://twitter.com/stewartknapman).

These opinions are as follows:

**Fluid Type:** This will increase the font size as the screen size increases. [Read more about this on Trent Waltons site here](http://trentwalton.com/2012/06/19/fluid-type/).

**Passing breakpoints from css to js:** This will add some breakpoint information to a sudo-class on the body tag which can be read in by Javascript (Javascript not included). [Jeremy Keith talks about this here](https://adactio.com/journal/5429).

**Pretty Underlines:** This will stop chromes underlines looking super chunky at larger font sizes. [Some discussion about this here](https://medium.com/designing-medium/crafting-link-underlines-on-medium-7c03a9274f9).

## Grids & Breakpoints

*TODO: Describe the percentage based grids and how to use them as well as how to setup custom breakpoints and col-sizes.*