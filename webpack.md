# Webpack

- `npm i --save-dev webpack webpack-cli webpack-dev-server typescript ts-loader`

On your project create a new file `webpack.config.js` with the following code

### Development workflow

```js
const path = require("path");

module.exports = {
  mode: "development",
  entry: "./src/app.ts",
  output: {
    filename: "bundle.js",
    path: path.resolve(__dirname, "dist"),
    publicPath: "dist",
  },
  devtool: "inline-source-map",
  module: {
    rules: [
      {
        test: /\.ts$/,
        use: "ts-loader",
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: [".ts", ".js"],
  },
};
```

### Production workflow

On your project create a new file `webpack.config.prod.js` with the following code

- `npm i --save-dev clean-webpack-plugin`

```js
const path = require("path");
const CleanPulign = require("clean-webpack-plugin");

module.exports = {
  mode: "production",
  entry: "./src/app.ts",
  output: {
    filename: "bundle.js",
    path: path.resolve(__dirname, "dist"),
  },
  devtool: "none",
  module: {
    rules: [
      {
        test: /\.ts$/,
        use: "ts-loader",
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: [".ts", ".js"],
  },
  plugins: [new CleanPulign.CleanWebpackPlugin()],
};
```

Now on your `package.json` you need to the add the following scripts

```json
"start": "webpack-dev-server",
"build": "webpack --config webpack.config.prod.js"
```
