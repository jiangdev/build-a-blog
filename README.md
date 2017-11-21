# build-a-blog
A learning project that steps through the process of building a blog using node, react/redux, and mongo. This is meant to deconstruct all of the parts of setting up a project from scratch, from the package json to the webpack config.

## Installation

```bash
$ git clone https://github.com/jiangdev/build-a-blog.git
$ cd build-a-blog
$ npm install
```

## Package Json Deconstructed

### react
A JavaScript library for building user interfaces. You use React to define and create your elements, for lifecycle hooks, etc. i.e. the guts of a React application

### react-dom
ReactDOM is the glue between React and the DOM. Often, you will only use it for one single thing: mounting with ReactDOM.render(). Another useful feature of ReactDOM is ReactDOM.findDOMNode() which you can use to gain direct access to a DOM element. (Something you should use sparingly in React apps, but it can be necessary.) If your app is "isomorphic", you would also use ReactDOM.renderToString() in your back-end code.

### webpack
Webpack is a module bundler, it bundles various module formats primarily so they can be run in a browser. It offers both a CLI and Node API.

### webpack-dev-server
Webpack Dev Server is itself an express server which uses ```webpack-dev-middleware``` to serve the latest bundle and additionally handles hot module replacement (HMR) requests for live module updates in the client.

### babel-cli
Babel's command line tools. It's recommended to install these per project rather than globally because different projects on the same machine can depend on different versions of Babel allowing you to update one at a time. It also means you do not have an implicit dependency on the environment you are working in. Making your project far more portable and easier to setup.

### babel-core
Babel's core compiler. Transforms your next-gen javascript code into code that older browsers can understand.

### babel-polyfill
Since Babel only transforms syntax (like arrow functions, destructuring, default arguments, and other syntax-specific features introduced in ES6), you can use babel-polyfill in order to support new globals such as Promise and WeakMap, as well as new static methods like Array.from or Object.assign

### babel-loader
The babel loader allows us to specify which files to load and transpile with babel and webpack. These configurations can be specified in the ```webpack config```

babel loader configuration example:
```json
module: {
  loaders: [
    {
      loader: "babel-loader",
      exclude: /node_modules/,
      include: [
        path.resolve(__dirname, "src"),
      ],
      test: /\.jsx?$/,
      query: {
        presets: ['react', 'env'],
      }
    },
  ]
}
```
```loader:``` specifies that we will be using the babel-loader to transpile our javascript code.

```exclude:``` allows us to blacklist files or directories from being transpiled. The example skips the node modules. Typically node modules are already transpiled so we don't need to process them again.

```include:``` allows us to whitelist files or directories from being transpiled. The example includes files only within the ```src``` directory. This may be more optimal as it allows you to transpile only the files that need to be transpiled.

```test:``` allows us to specify what file extensions to pass through Babel. The example only runs `.js` and `.jsx` files through Babel.

```query:``` options to configure babel with. These presets can be specified in the babelrc

### babel-plugin-transform-object-rest-spread
Transform rest properties for object destructuring assignment and spread properties for object literals.

Rest Properties:
```javascript
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }
```

Spread Properties:
```javascript
let n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```

### babel-preset-env
Babel preset that automatically determines the Babel plugins you need based on your supported environments. Uses compat-table. Without any configuration options, babel-preset-env behaves exactly the same as babel-preset-latest (or babel-preset-es2015, babel-preset-es2016, and babel-preset-es2017 together).

Without babel-preset-env, we would have to install these packages to support specific environments:
```bash
# For ES6/ES2015 support
npm install babel-preset-es2015 --save-dev
```
```bash
# If you want to use experimental ES7 features
npm install babel-preset-stage-0 --save-dev
```

### babel-preset-react
Strip flow types and transform JSX into createElement calls. Allows us to use JSX.
```bash
npm install babel-preset-react --save-dev
```

# Sources
[React & ReactDOM](https://stackoverflow.com/a/34114665)

[Webpack & Webpack Dev Server](https://stackoverflow.com/a/42354413)

[Babel CLI](https://babeljs.io/docs/usage/cli/)

[Babel Presets & Setup](https://babeljs.io/blog/2015/10/31/setting-up-babel-6)

[Babel Loader](http://jamesknelson.com/using-es6-in-the-browser-with-babel-6-and-webpack/)

[Polyfill](https://hackernoon.com/polyfills-everything-you-ever-wanted-to-know-or-maybe-a-bit-less-7c8de164e423)

[Transform Object Rest Spread](https://babeljs.io/docs/plugins/transform-object-rest-spread/)
