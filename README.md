# Lyas

> An elegant way to define your CSS variables in all their forms

[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/VeronQ/lyas/blob/master/LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/veronQ/lyas/graphs/commit-activity)

**Version** [v1.0.5](https://github.com/VeronQ/lyas/releases)

Lyas is a Sass-based library which provide an alternative solution to define your CSS variables and their values depending of the current device-width.

## Installation

#### NPM

``` sh
$ npm install lyas
```

#### Download

See https://github.com/VeronQ/lyas/blob/1.0.5/lyas.scss

#### CDN

See https://cdn.jsdelivr.net/npm/lyas@latest/lyas.scss

## Usage

###### 1. Import Lyas at the beginning of your stylesheet

``` scss
@import '<path-to>/lyas';
```

###### 2. Set your CSS variables using the pre-defined `var-mq` mixin.

``` scss
@include var-mq('--text-color',
  $default: red,
  $md: blue,
  $lg: green
);
```

###### 3. Use your CSS variables as you would usually do.

``` scss
.foo {
  color: var(--text-color);
}
```

###### 4. Inject all the CSS variables defined with `var-mq` into the `:root selector`. *[Must be placed at the very end of your file]*

``` scss
@include init-lyas;
```
---

The example above from the *second-point* will be compiled into:

``` css
:root {
  --text-color: red;
}

@media screen and (min-width: 768px) {
  :root {
    --text-color: blue;
  }
}

@media screen and (min-width: 992px) {
  :root {
    --text-color: green;
  }
}
```

## Options

### @var-mq

The `var-mq` mixin takes multiple arguments.

| Variable         | Required      | Description               |
| :--------------- | :------------ | :------------------------ |
| $custom-property | Yes           | Variable name             |
| $default         | Yes           | Default value             |
| $sm              |               | Small devices value       |
| $md              |               | Medium devices value      |
| $lg              |               | Large devices value       |
| $xl              |               | Extra large devices value |



### $breakpoints

By default, Lyas comes with four pre-defined breakpoints:

* `sm`: 576px
* `md`: 768px
* `lg`: 992px
* `xl`: 1200px

You can easily change those values by defining a new `$breakpoints` map which will override the default one.

``` scss
// A new defined breakpoints map (Materialize.css)
$breakpoints: (
  'sm': null,
  'md': 600px,
  'lg': 992px,
  'xl': 1200px
);
```

> You can choose to omit some breakpoints (as the `sm` in the example) but you still have to set their value to `null`.

## License
[MIT](https://github.com/VeronQ/lyas/blob/master/LICENSE)
