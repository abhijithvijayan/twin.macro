# Use Twin with Create React App + Emotion

**🔥 View the [CRA + Emotion + Tailwind Twin starter](https://codesandbox.io/embed/cra-tailwind-emotion-starter-bi1kx?module=%2Fsrc%2FApp.js) for setup and usage examples**

## TypeScript

Twin comes with built-in TypeScript types for `tw`.
To support Twin's `css` and `styled` imports, check out our [Emotion + TypeScript guide](typescript.md) once you've finished with the installation below.

## Installation

### 1. Install Create React App

```bash
npx create-react-app my-app
```

### 2. Install the dependencies

```bash
npm install --save twin.macro @emotion/core @emotion/styled
```

<details>
  <summary>Yarn instructions</summary>

```bash
yarn add twin.macro @emotion/core @emotion/styled
```

</details>

### 3. Import the Tailwind base styles

Add the following to your `app.js` or `index.js`:
(the dependency 'tailwindcss' is already in your node_modules)

```js
// In your App.js or index.js entry
import 'tailwindcss/dist/base.min.css'
```

### 4. Configure custom config location

Place tailwind.config.js in the `src` folder. This allows it to be imported by a theme provider:

```js
// package.json
"babelMacros": {
  "twin": {
    "config": "src/tailwind.config.js"
  }
},
```

<details>
  <summary>Alternatively add config to babel-plugin-macros.config.js</summary>

```js
// babel-plugin-macros.config.js
module.exports = {
  twin: {
    config: 'src/tailwind.config.js',
  },
}
```

</details>

### Basic usage example

```js
import 'twin.macro'
export default () => <button tw="text-lg px-8 py-2 rounded">Success</button>
```

More usage examples can be found in the [CRA + Emotion + Tailwind Twin starter](https://codesandbox.io/embed/cra-tailwind-emotion-starter-bi1kx?module=%2Fsrc%2FApp.js).

## Configuration

<details>
  <summary>Customize the Tailwind classes</summary>

### Customize the Tailwind classes

For style customizations, you’ll need to add a `tailwind.config.js` in your project root.

> It’s important to know that you don’t need a `tailwind.config.js` to use Twin. You already have access to every class with every variant.
> Unlike Tailwind, twin.macro only generates styles for the classes you use. This means you don’t need to use additional tools like purgeCSS.

Choose from one of the following configs:

- a) Start with an empty config:

  ```js
  // tailwind.config.js
  module.exports = {
    theme: {
      extend: {},
    },
  }
  ```

- b) Start with a [full config](https://raw.githubusercontent.com/tailwindcss/tailwindcss/master/stubs/defaultConfig.stub.js):

  ```bash
  # cd into your project folder then:
  curl https://raw.githubusercontent.com/tailwindcss/tailwindcss/master/stubs/defaultConfig.stub.js > tailwind.config.js
  ```

  In the config, there only needs to be a `theme: {...}` entry so feel free to cleanup.

### Working with the config

You can overwrite or extend classes the same way as Tailwind.<br/>
Overwrite parts of the base config in `theme: { ... }` and extend in `theme: { extend: { ... } }`.<br/>
Read more in the [Tailwind theme docs](https://tailwindcss.com/docs/theme).

<hr />

</details>

<details>
  <summary>Configure Twin</summary>

### Configure Twin

These defaults can be added to your `package.json`:

```js
// package.json
"babelMacros": {
    "twin": {
      "config": "./tailwind.config.js",
      "preset": "emotion",
      "hasSuggestions": true,
      "debug": false,
    }
},
```

Alternatively add the config to `babel-plugin-macros.config.js` in your project root:

```js
// babel-plugin-macros.config.js
module.exports = {
  twin: {
    config: './tailwind.config.js',
    preset: 'emotion',
    hasSuggestions: true,
    debug: false,
  },
}
```

| Name           | Type      | Default                  | Description                                                                 |
| -------------- | --------- | ------------------------ | --------------------------------------------------------------------------- |
| config         | `string`  | `"./tailwind.config.js"` | The path to your Tailwind config                                            |
| preset         | `string`  | `"emotion"`              | The css-in-js library behind the scenes - also supports 'styled-components' |
| hasSuggestions | `boolean` | `true`                   | Display class suggestions when a class can't be found                       |
| debug          | `boolean` | `false`                  | Display information about the Tailwind class conversions                    |

If Twin's default `styled` and `css` imports need to be adjusted, you can do so with the following config:<br/>

```js
{
  styled: { import: "default", from: "@emotion/styled" },
  css: { import: "css", from: "@emotion/core" }
}
```

**Note:** Make sure you remove the `preset` option as that value disables the styled + css options.

<hr />

</details>

## Emotion resources

- [The css prop](https://emotion.sh/docs/css-prop)
- [The css import](https://emotion.sh/docs/css-prop#string-styles)
- [The styled import](https://emotion.sh/docs/styled)

## Other installation guides

- ["Vanilla" React + Emotion](react.md)
- [Gatsby + Emotion](gatsby.md)
- [Next.js + Emotion](next.md)
