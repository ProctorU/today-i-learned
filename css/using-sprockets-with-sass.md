#### Using Sprockets With Sass

In Rails, it's common to `@import` all of your SASS partials like below:

```scss
// application.css.scss
@import "base/variables";
@import "base/mixins";
@import "components/buttons";
@import "components/cards";
@import "libraries/bootstrap-datepicker"
```

As you continue to add more and more SASS files, the compile time starts to add
up, because it is recompiling all of your files. Ouch! Our compile time was
taking anywhere from 30-40 seconds.

**Sprockets to the rescue!**

When you require your SASS partials with sprockets, the only compile that takes
place is the file you changed. See below:

```scss
// application.css.scss

//= require components/_buttons

-------------------------------
// _base.scss
//= require base/_variables
//= require base/_mixins

-------------------------------
// components/_buttons.scss
@import "base";

.button {
  ...
}
```

The main difference here is now we are including our variables, mixins, and
function partials on each component partial. Seems a bit redundant at first,
but it lets you know exactly what that file has access to.

Our compile time is now < 3 seconds.
