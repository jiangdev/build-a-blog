# build-a-blog
A learning project using node, react/redux, and mongo.

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

# Sources
[React & ReactDOM](https://stackoverflow.com/a/34114665)

[Webpack & Webpack Dev Server](https://stackoverflow.com/a/42354413)
