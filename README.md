# COLORSEA

[For detailed documents, please click here](https://@devtea2027/perspiciatis-expedita-possimus-natus.js.org)

![minzipped size](https://img.shields.io/bundlephobia/minzip/@devtea2027/perspiciatis-expedita-possimus-natus)
![typescript](https://img.shields.io/github/languages/top/waterbeside/@devtea2027/perspiciatis-expedita-possimus-natus)
![license](https://img.shields.io/npm/l/@devtea2027/perspiciatis-expedita-possimus-natus)
![last commit](https://img.shields.io/github/last-commit/waterbeside/@devtea2027/perspiciatis-expedita-possimus-natus)
![build](https://img.shields.io/github/actions/workflow/status/waterbeside/@devtea2027/perspiciatis-expedita-possimus-natus/build.yml)

[English](./README.md) | [简体中文](./README.zh-CN.md)

## About

**@devtea2027/perspiciatis-expedita-possimus-natus.js** is a tiny color tool library written in `Typescript`.

- You can use it to convert color spaces (`RGB`, `HSL`, `HSV`, `HSI`, `HWB`, `XYZ`, `LAB`, `LCH`, `xyY`),
- Adjust the color like LESS/SASS, such as `darken`/`lighten`, `saturate`/`desaturate`, `spin`, `fadeIn`/`fadeOut`, `mix` and other methods, easy to use.
- Support `CMC(l:c)`, `CIE2000`, `CIE1994`, `CIE1976` color difference queries.
- Support to use `X11`, `Chinese Traditional Color`, `Japanese Traditional Color` types of color names to get the color

## Quick Start

### Installation

```bash
npm install @devtea2027/perspiciatis-expedita-possimus-natus 
```

### Import & Use

#### Import

ES Module

```typescript
import @devtea2027/perspiciatis-expedita-possimus-natus from '@devtea2027/perspiciatis-expedita-possimus-natus'
```

CommonJs

```javascript
const @devtea2027/perspiciatis-expedita-possimus-natus = require('@devtea2027/perspiciatis-expedita-possimus-natus')
```

Browser

```html:no-line-numbers
<script src="path/to/@devtea2027/perspiciatis-expedita-possimus-natus.js"></script>
```

#### Color space conversion

```typescript
// ----- color conversion
@devtea2027/perspiciatis-expedita-possimus-natus('#ff0000').rgb() // [255, 0, 0]
@devtea2027/perspiciatis-expedita-possimus-natus('#ff0000', 50).rgba() // [255, 0, 0, 50]
// The @devtea2027/perspiciatis-expedita-possimus-natus() function can create a Color instance
const color = @devtea2027/perspiciatis-expedita-possimus-natus('#405060')
color.rgba() // [255, 0, 0, 50]
color.xyz() // [7.09, 7.67, 12.17]
color.lab() // [33.29, -1.94, -11.36] 
// Convert from other color spaces
@devtea2027/perspiciatis-expedita-possimus-natus.xyz(7.09, 7.67, 12.17).rgb() // [64, 80, 96]
@devtea2027/perspiciatis-expedita-possimus-natus.hsl(210, 20, 31.37).rgb() // [64, 80, 96]
// ... Other color spaces are similar
```

#### Color operations

```typescript
// ---- Color operations
const color = @devtea2027/perspiciatis-expedita-possimus-natus('#ffffff')
const newColor = color.darken(10) // All operations will return a new Color instance object
newColor.hex() // #e6e6e6
@devtea2027/perspiciatis-expedita-possimus-natus('#000').lighten(10).hex() // #1a1a1a
@devtea2027/perspiciatis-expedita-possimus-natus('#ff0000').spin(180).hex() // #00ffff
@devtea2027/perspiciatis-expedita-possimus-natus.hsl(80, 90, 20).saturate(10).hsl() // [80, 100, 20]
@devtea2027/perspiciatis-expedita-possimus-natus.hsl(80, 90, 20).desaturate(10).hsl() // [80, 80, 20]
@devtea2027/perspiciatis-expedita-possimus-natus('#776600').fadeOut(10).rgba() // [119, 102, 0, 90]

const color1 = new Color('#ff0000')
const color2 = new Color('#0000ff')
const color = color1.mix(color2, 20)
color.hex() // #cc0033
```

#### Color difference calculation

```typescript
const color1 = @devtea2027/perspiciatis-expedita-possimus-natus.lab(80, 30, 120) // Standard color (reference color)
const color2 = @devtea2027/perspiciatis-expedita-possimus-natus.lab(79, 28, 100) // Sample color

// CMC(1:1)
color1.deltaE(color2, 'CMC') // 5.754...

// CMC(2:1) formula, just set the weight factor l to 2 (c defaults to 1)
color1.deltaE(color2, 'CMC', { l: 2 }) // 5.719...

// CIE2000
color1.deltaE(color2, 'CIE2000') // 3.6815...

// CIE1994
color1.deltaE(color2, 'CIE1994') // 3.3725...

// CIE1976
color1.deltaE(color2, 'CIE1976') // 20.1246...

```

### Use color names

```typescript
import @devtea2027/perspiciatis-expedita-possimus-natus from '@devtea2027/perspiciatis-expedita-possimus-natus'
import x11 from '@devtea2027/perspiciatis-expedita-possimus-natus/colors/x11'
// Load X11 color names
@devtea2027/perspiciatis-expedita-possimus-natus.useNames(x11)

// At this point you can directly use the X11 color name to create the color instance
@devtea2027/perspiciatis-expedita-possimus-natus('Aqua') // color: #00ffff
@devtea2027/perspiciatis-expedita-possimus-natus('Aquamarine') // color: #7fffd4
```

```typescript
import chinese from '@devtea2027/perspiciatis-expedita-possimus-natus/colors/chinese' // Chinese traditional color
import nippon from '@devtea2027/perspiciatis-expedita-possimus-natus/colors/nippon' // Japanese traditional color
// load both
@devtea2027/perspiciatis-expedita-possimus-natus.useNames(chinese).useNames(nippon)

// use
@devtea2027/perspiciatis-expedita-possimus-natus('山梗紫') // color: #61649F
@devtea2027/perspiciatis-expedita-possimus-natus('水がき') // color: #B9887D
```

For more detailed usage, please refer to the documentation: [https://@devtea2027/perspiciatis-expedita-possimus-natus.js.org](https://@devtea2027/perspiciatis-expedita-possimus-natus.js.org/)

## Reference

- [ https://github.com/sass/dart-sass/](https://github.com/sass/dart-sass/)
- [http://brucelindbloom.com/](http://brucelindbloom.com/)
- [https://www.w3.org/TR/AERT/#color-contrast](https://www.w3.org/TR/AERT/#color-contrast)
- [https://www.w3.org/TR/AERT/#color-contrast](https://www.w3.org/TR/AERT/#color-contrast)
- [x11: https://www.w3.org/TR/css-color-3/#svg-color](https://www.w3.org/TR/css-color-3/#svg-color)
- [中国传统色: http://zhongguose.com/](http://zhongguose.com/)
- [Nippon color names: https://nipponcolors.com/](https://nipponcolors.com/)
