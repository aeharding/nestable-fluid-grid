Nestable Fluid Grid
=====================
Compass / SASS set of mixins for an infinitely nestable fluid grid.

* Assign column width, gutter width, and number of columns.
* Mixins included for container, row, and column span.
* Infinitely nestable.
* Gutter width stays visually consistent when nested.
* No *alpha*, *omega*, or *nth-child* needed on end columns.
* Columns flow naturally to the next row when the number of column spans exceed the width of the row.
* Mixin based, so class names are flexible.

### Installation
The only file needed for the grid is sass/partials/_grid.scss. Everything else is just for the demonstration. Compass is not required. Simply include the _grid.scss file anywhere within an existing Compass or SASS project.
    
    @include "partials/grid.scss";

### Configure Grid Settings
Configure the grid by setting the 4 variables.

    // Configure grid variables in _grid.scss
    
    $totalColumns:      12;
    $gutterWidth:       1em;
    $columnWidth:       6em;
    $containerPadding:  1em;
    
    // Apply mixins to any class
    
    @include container;     // Applies container max-width and padding
    @include row(12)        // Defines a row that spans 12 columns
    @include spans(2,12)    // Defines a column that spans 2 columns
                            // widths within a 12 column row.

### Nesting

To nest a grid, create another row within a span. The parameter given to the nested row should its parent span's assigned width. Example:
    
    @include row(12);       // Row spanning 12 columns.
    @include spans(4,12);   // Column spanning 4 columns.
    @include row(4);        // Nested row inside our span(4,12)
    @include spans(2,4);    // Nested columns spanning 2 of 4 columns.

### Markup Structure
Markup structure should follow a row > span structure. Example:

    div.container
        div.row
            div.span
            div.span
            div.span
                div.row
                    div.span
                    div.span
                    div.span
            div.span
            div.span
