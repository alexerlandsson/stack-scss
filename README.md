# Stack SCSS

Experimental stack component used to stack elements horizontally and vertically using _CSS_ `flexbox` and `gap` properties. Everything needed to stack elements is to wrap them in a containing node.

```html
<div class="stack">
  <!-- Stacked content goes here -->
</div>
```

## How to use

Include the folder `src/stack` in your _scss_ project and import the component using `@use` targeting `stack/index.scss`.

```scss
@use "[PATH]/stack" as *;
```

## Settings

This component utilizes _BEM_ modifiers to customize the settings of the stack.

### Direction

Use these modifiers to set which direction the items should stack. The direction is set using `flex-direction` and is unset by default. This means children will align horizontally if direction is not set.

#### Horizontal

`.stack--horiztonal` will stack the elements on the horiztonal axis.

```html
<div class="stack stack--horizontal"></div>
```

#### Vertical

`.stack--vertical` will stack the elements on the vertical axis.

```html
<div class="stack stack--vertical"></div>
```

### Spacing

The spacing modifier is used to add spacing between each item. The spacing between all items in the same `.stack` will always be the same. If you want to have different spacing between items in the same stack you can nest mutliple stacks inside each other.

Spacing is by default set by the `size()` function found in `src/helpers/_functions.scss` and is based on a base unit (default `8px`). The different sizes available are set using the `$stack-sizes` variable. Available spacing by default are `1, 2, 3, 4, 5`.

> **Note:** The size of the output _CSS_ will increase if adding more spacing options. It is recommended to only include sizes used in the project.

#### Usage of spacing

To add spacing of one base unit (8px * 1 = 8px), add the modifier `.stack--spacing-1`. In the example below, all items will have a spacing of `8px` between them.

```html
<div class="stack stack--spacing-1"></div>
```

To add spacing of two base units (8px * 2 = 16px), add the modifier `.stack--spacing-2`. In the example below, all items will have a spacing of `16px` between them.

```html
<div class="stack stack--spacing-2"></div>
```

_And so on..._

### Alignment

Alignment is set using block and/or inline alignment. Just as CSS logical properties, block alignment will align on the horizontal axis for horizontal stacks and on the vertical axis on vertical stacks. The same rule applies to inline alignment but the other way around.

Available alignments are set in the `$stack-align` map. Available alignments by default are:

* start (flex-start)
* center
* end (flex-end)

#### Block alignment

Use the modifier `.stack--aling-block-[ALIGN]` to add block alignment.

```html
<div class="stack stack--align-block-start"></div>
```

#### Inline alignment

Use the modifier `.stack--aling-inline-[ALIGN]` to add inline alignment.

```html
<div class="stack stack--align-inline-start"></div>
```

### Separate last child

Coming soon...

### Breakpoint specific settings

All modifiers are set up with breakpoint specific selectors to make it possible to use a specific setting in a specific breakpoint. The selectors are structured as `.stack--[MODIFIER]:[BREAKPOINT_NAME]`. Available breakpoints are set in the `$breakpoints` variable in `src/helpers/_breakpoints_.scss`.

#### Usage of breakpoint specific settings

The example below shows how to set the stack to be vertical by default and switch to horiztonal in the breakpoint `md`.

```html
<div class="stack stack--vertical stack--horizontal:md">
```

## Work in this repository

Before you start working in this repository, install the dependencies.

```bash
npm install
```

### Compile scss to CSS

Compile the _scss_ in this project into _CSS_ by running the following commands.

```bash
npm run sass
```

The scripts will output a _CSS_ file at `dist/stack.css`.

### Code formatting

This project uses [Prettier](https://prettier.io/) to format the code. To format all files, run the following command.

```bash
npm run prettier
```

### Lint

This project uses [Stylelint](https://stylelint.io) to lint the _scss_. The settings is based on `stylelint-config-standard-scss`. To run the lint, run the following command.

```bash
npm run stylelint
```
