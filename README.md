# webpack-setup

This repository is used for understanding the process of setting up a webpack config file for a React project.

## Common questions:

### What is webpack?
Webpack is a module bundler for JavaScript applications. Its common features are:
1. Module Bundling
2. Loaders -> Used to preprocess files before bundling
3. Plugins -> Used post bundling to perform additional tasks

## DEV vs PROD mode
What happens in dev mode? - When we run in dev mode the bundle.js will be created in memory(RAM) and served for faster and efficient operations during development.

What happens in prod mode? - When we run in dev mode the bundle.js will be created in disk.

After the creation of bundle.js, we need to reference it using `<script>` tag in index.html, handled by `HTMLWebpackPlugin` configured inside `webpack.config.js`.


## Explaining webpack config file

We begin with importing the path module, which is used to work with file and directory paths.
```
import { path } from path;
```

Specifically, the path.resolve() method is used to create an absolute path to the output directory.
```
 output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
```
` Note: __dirname is special variable in Node.js that provides the absolute path of the directory containing the currently executing script. In this case, it would ~/code/webpack-setup.`

### Fields & their meanings:
- entry: Defines the entry point of the application, webpack will start bundling from this file.
- output
    1. path: Specifies the directory where webpack should place the bundled files.
    2. filename: Specifies the name of the bundled file. In this case, the bundled JavaScript file will be named 'bundle.js' and will be placed in the 'dist' directory.
- module: This field is used to specify how webpack should process different types of files.
    1. rules: An array of rules where each rule defines how a specific type of file should be processed.
        - use: The use field specifies the loader (babel-loader) and its options. It tells webpack to use Babel for transpiling JavaScript code, with presets for handling React and modern JavaScript features.


## Steps to create this repository locally -

### Step 1: Initialize a git repository

This step is used to initialize a git repository locally
```
git init
```
### Step 2 : Initialize npm project

This step is used to initialize a basic npm project
```
npm init -y
```
### Step 3: Install webpack dev-dependencies

Webpack is a module bundler for JavaScript applications.
```
npm install webpack webpack-cli --save-dev
```
### Step 4: Install react dependencies 

The JavaScript library for building user interfaces.
```
npm install react react-dom --save
```
### Step 5 : Install Babel(transpiler) 

This helps us support latest version of JS on older browser
```
npm install babel-loader @babel/core @babel/preset-env @babel/preset-react --save-dev
```
### Step 6: Webpack Dev Server

Helps us in live reloading of app
```
npm install webpack-dev-server --save-dev
```
### Step 7: HTML Webpack plugin
Simplifies the creation of an HTML file to include your webpack bundles.
```
npm install html-webpack-plugin --save-dev
```
### Step 8 : CSS loaders
If you plan to use CSS in your React project.
```
npm install style-loader css-loader --save-dev
```
### Step 9 : File loader
To handle static assets like images or fonts
```
npm install file-loader --save-dev
```
### Step 10: Add scripts

Modify the scripts property in package.json to start & build webpack server
```
"scripts": {
  "start": "webpack serve --mode development --open",
  "build": "webpack --mode production"
}
```

### Step 11: Creating index.js & App.js in src
```
mkdir src
cd src
touch index.js
touch App.js
```

### Step 12: Add basic index.html under public directory
```
mkdir public
touch index.html
```
