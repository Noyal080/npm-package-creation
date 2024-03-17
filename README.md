
### Create NPM Package using Webpack and Babel

##### Steps to follow :
    1) mkdir add-package (suppose a package-name add-package)
    2) cd add-package
    3) npm init -y
    4) npm install react react-dom --save-dev
    5) In package.json you see a devDependencies now copy the react and react dom and create an object 
        peerDependencies and paste it.
          ```
          "peerDependencies": {
            "react": "^18.2.0",
            "react-dom": "^18.2.0"
            },
          ```
    6) Create a folder named src and create your component file.
        Your folder structure right now looks like: 
            my-package/
            └── node-modules
                ├── src/
                │   ├── index.js
                │   ├── module1.js
                │   └── module2.js
            └── package.json
    7) Create the components you want, then in index.js code as folow:-
    ```
        export {default as Module1} from "./module1.js"     
        export {default as Module2} from "./module2.js"  
    ``` 
    8) Now you want to install webpack webpack cli and babel
               npm install @babel/core @babel/preset-env @babel/preset-react
               babel-loader webpack webpack-cli --save-dev
    9) In your folder root structure create .babelrc: 
       ``` 
       {  "presets": ["@babel/preset-env", "@babel/preset-react"]
        }
        ```
    10) Also create a webpack.config.js :
        ```
          const path = require("path");
          module.exports = {
              entry: "./src/index.js",
              output: {
                  path: path.resolve(__dirname, "dist"),
                  filename: "bundle.js",
                  libraryTarget: "umd",
                  library: "add-package",
                  umdNamedDefine: true,
              },
              mode: "development",
              module: {
                  rules: [
                  {
                      test: /\.js$/,
                      exclude: /node_modules/,
                      use: {
                      loader: "babel-loader",
                      },
                  },
                  ],
              },
              };
        ```
    11) In your package.json inside script add a build: 
         ```
         scripts": {
                   "test": "echo \"Error: no test specified\" && exit 1",
                   "build": "webpack"
                },
        ```
    12) In terminal press command npm run build
    13) Then npm login and use your npmjs.com login credentials
    14) Use command npm publish to publish your package
#### While using css for styling in the package add the below code in `webpack.config.js`
     {
        test: /\.css$/,
        use: ["style-loader", "css-loader"],
      },
#### For updating the code :
     15) npm run build
     16) npm version patch // This add a patch to your build version 
         OR you can specify version 
         npm version 1.2.0
    17 ) npm publish
