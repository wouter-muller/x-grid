# X-GRID

## Fully dynamic, lightweight, responsive and semantic grid

### Dynamic
You can create any kind of grid you want, a 10-column grid, a 12-column grid, or
even a 99-column grid. You can pass along margins and paddings to the grid and
columns, so you keep everything in 1 place.

### Lightweight

The `.scss` file is only 100 lines (including comments) long, so you are not adding
bloat to your code.

### Responsive
This grid uses percentages, so they adapt automatically to the space they get. For
mobile, you can use special classes so you can position the content in a different
way for mobile.

### Semantic
This grid makes it possible to use semantic classes and specify all the grid-related
styles inside the CSS. This way you don't have to clutter up your markup with
presentational style classes.

### Example:

A simple grid with a sidebar and a content area:

HAML:
```
%section
  .sidebar
  .content-area
```
SASS:
```
%section {
  @include x-grid;

  .sidebar {
    @include x-col-3-12;
  }
  .content-area {
    @include x-col-9-12;
  }
}
```
If you don't have semantic classes to work with, you can also
add grid classes to the markup, this way you don't have to write
any CSS, but you do clutter up your markup with presentational
classes. But it is possible, like this:

HAML:
```
.x-grid
  .x-col-3-12
  .x-col-9-12
```
### Mobile modifier classes
If you don't specify a mobile class, each column will just get 100% width,
which is, in most cases, what you want. If you do want to position things
side by side on mobile, you can do the following:

HAML:
```
.x-grid
  .x-col-6-12.x-col-m-2-4
  .x-col-6-12.x-col-m-2-4
```
### Extra options

- Add margin to the grid:
`@include x-grid($margin: 0 0 20px 0); // adds 20px margin-bottom`
- Add padding to the grid:
`@include x-grid($padding: 50px 0); // adds 50px top and bottom padding`
- Change gutter size between columns:
`@include x-col(6, 12, $gutter: 4%); // 6 cols inside a 12-col grid, with 4% gutter`
- Add padding to columns:
`@include x-col(6, 12, $padding: 1rem); // columns get 1rem (generally 16px) padding`
- Move columns to any position (or even change the order they appear in):
```
@include x-move(4, 12); // puts the column on the 4th position in a 12-column grid
@include x-move(1, 12); // puts the column on the 1st position even if it is not
                        // the first column in the markup
```
- A grid always has to start with `.x-grid` or a semantic class that uses the
  x-grid mixin
- A grid's direct children should only be columns, inside the columns you can put
  anything
