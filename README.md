# Bootstrap container as a (css display) table

Makes bootstraps grid markup behave as table layout.

Uses bootstrap's breakpoint column classes. For example a column within a `.container-table` with `.col-sm-6` with only act as a table cell from small breakpoint and above.

## Requirements

The base rules for bootstrap grid from either the default build or the bootstrap sass library.

The sass mixins allow you to choose how much to output, for example if you only want a container-table from breakpoint md and up you can `@include container-md-table`.

If you just want to drop all the rules into the default bootstrap.css use the file: `bootstrap-container-table.css`

The container element requires the base `container` class in addition to the `container-table` class. Rows and Columns only require standard bootstrap classes.

Example:

```
&lt;div class="container container-table"&gt;
    &lt;div class="row"&gt;
        &lt;div class="col-sm-6 vertical-middle"&gt;
            
        &lt;/div&gt;
        &lt;div class="col-sm-6 vertical-middle"&gt;
            
        &lt;/div&gt;
    &lt;/div&gt;    
&lt;/div&gt;
```

## Available mixins

These mixins will include @media wrappers for the bootstrap breakpoints.

* `@include container-lg-table`
* `@include container-md-table`
* `@include container-sm-table`
* `@include container-xs-table`

## Caveats

* Obviously only compatible with browsers that support `display: table` `display: table-row` and `display: table-cell`.
* Is written to only affect direct decendants ie. `.container-table > .row .col-sm-6` etc.
* An image in a cell that is larger than the cells width as set by column class will force the cell larger to the images native size even when it has `max-width: 100%` in Firefox and IE, Chrome keeps the image contained in the cells width. The only way I've found to fix this setting the img to `width:100%` which is fine for images >= the cell width but would obviously be undesirable to timy images.


## Example

The example doesn't use bootstraps sass files but does contain the bootstrap default. The output css is compatible with vanilla bootstrap v3.