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

This path is reletive to where your main scss file is stored within your project, so if your file is within `src/scss/styles.scss` then the path to inside will look like this: `'../../node_modules/inside-scss/src/inside'`.

**Step 3:** Profit!

## Globals & Modules

### Classes

Everything in Inside is a mixin. This way it can be as light and modular as you need, however each mixin has its own class for convenience.

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

## Breakpoints, Containers & Grids

### Breakpoints

By default there are four breakpoints: `$breakpoint_sm`, `$breakpoint_md`, `$breakpoint_lg` and `$breakpoint_xl`, these can be set with variables. Anything below `$breakpoint_sm` is considered `xs`.

However you can create your own breakpoints and have as many as you want or need. This is done with a nested list* like this:

```
$breakpoint_sizes: (xs false) (sm $breakpoint_sm) (md $breakpoint_md) (lg $breakpoint_lg) (xl $breakpoint_xl);
```

The first item for each list item is the key, this will be used when passing breakpoints (see opinion above) and for constructing your grid classes.
The second item for each list item is the breakpoint to be used. The first list item has no breakpoint as this will happen before the first one kicks in. 

Note: if you do change the breakpoints you will also need to create `$container_width_` and `$grid_gutter_` variables to match your breakpoint keys.

### Containers

Containers can either be set as a class on your container element: `.container` or with a mixin: `.container { @include container; }` if you don't want to include the base classes.

There are two types of containers: `.container` & `.container-fluid`. The fluid container is always 100% or what ever you set with the `$container_width_fluid` variable. The standard container has a percentage based width, which changes on each break point. You can also set the `$container_max_width` variable to constrain it's width e.g. (the default is false: no max width)

```
$container_max_width: 55em;
```

### Grids

Like all other things grids can be set by classes: `grid-col-[size]-[breakpoint]` e.g. `grid-col-50-xs` or by a mixin: `@include grid-col-size($size, $breakpoint);`. When using the mixin the second parameter, $breakpoint, is optional and defaults to false which will set just the width.
Be sure to include the `grid-col` or `grid-col-rev` base classes/mixins on your columns.

There is a default list* of grid columns for classes, much like breakpoints, which can be overridden. This allows you to include only the classes you want/need. The list items key will be used as the size portion of the class:

```
$col_sizes: (5 5%) (10 10%) (15 15%) (20 20%) (25 25%) (30 30%) (40 40%) (50 50%) (60 60%) (70 70%) (75 75%) (80 80%) (85 85%) (90 90%) (95 95%) (100 100%) (quarter 25%) (half 50%) (three-quarters 75%) (full 100%) (one-third 33.333%) (one-sixth 16.666%) (two-thirds 66.666%);
```

For more information on grids refer to [the grids section on the demo page](http://stewartknapman.github.io/inside/).

* I've used nested lists instead of maps as maps don't exists in versions of sass < 3.3. But why does that matter you ask? Because the version of sass that Shopify uses is < 3 and a lot of my work is with Shopify.