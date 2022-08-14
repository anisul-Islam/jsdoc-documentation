# jsdoc documentation

[Remember that I have already shown you how to use Prettier, ESLint]

- Reference:

  - [jsdoc](https://jsdoc.app/index.html)
  - [geeksforgeeks](https://www.geeksforgeeks.org/introduction-to-jsdoc/)

- what is jsdoc?
  - It is an API documentation generator for JavaScript.

## How to setup jsdoc generator in a project

- step 1: initialize npm: `npm init -y`
- step 2: install jsdoc: `npm install -g jsdoc` or `npm install -D jsdoc`
- step 4: add the following line of code in package.json

    ```json
        "scripts" : {
          "jsdoc" : "jsdoc -c jsdoc.json"
          // others
        }
    ```

- step 5: In the root of the project create jsdoc.json file and add the following codes

    ```json
    {
      "plugins": ["plugins/markdown"],
      "recurseDepth": 10,
      "source": {
        "include": ["src"],
        "includePattern": ".js$",
        "excludePattern": "(node_modules/|docs)"
      },
      "templates": {
        "cleverLinks": true,
        "monospaceLinks": true
      },
      "opts": {
        "destination": "./jsdoc",
        "recurse": true,
        "readme": "./readme.md"
      }
    }
    ```

- step 6: Running JSDoc: `npm run jsdoc`
- step 7: a jsdoc folder will be create from where you can find index.html and open it to any browser to navigate the generated documentation

## jsdoc tutorial

- for better type check just like typescript you can add following in your vscode settings.json

  ```json
  {
    "js/ts.implicitProjectConfig.checkJs": true
  }
  ```

- jadoc documentation

  ```javascript
  // variable documentation syntax

  /**
   * description
   * @type {typeName}
   */

  // variable documentation examples

  /**
   * user's fullName
   * @type {string}
   */
  const fullName = "Anisul Islam";

  /**
   * Array of users
   * @type {Array}
   */
  const users1 = ["Anisul Islam", "Robert", "David"];

  /**
   * Array of users age
   * @type {Array<number>}
   */
  const users2 = [24, 32, 18];

  /**
   * user details
   * @type {{name: string|number, age: number}}
   */
  const user = {
    name: "david",
    age: 32,
  };

  /**
   * user details
   * @type {Array<{name: string, age: number}>}
   */
  const users = [
    {
      name: "david",
      age: 32,
    },
    {
      name: "robert",
      age: 31,
    },
  ];

  // function documentation syntax
  /**
   * description goes here
   * @param {typeName} paramName  parameter description
   * @returns {typeName} description
   */

  // function documentation example
  // In the following example {*} refers to any type; we can also specify the type by saying name of the type

  /**
   * calulates the area of nothing
   * @returns {string} a simple text
   */
  function areaOfNothing() {
    return "area of nothing";
  }

  /**
   * calulates the area of triangle
   * @param {*} dim1 the base of the triangle
   * @param {*} dim2 the height of the triangle
   * @returns {number} area of triangle
   */
  function areaOfTriangle(dim1, dim2) {
    return 0.5 * dim1 * dim2;
  }

  /**
   * calulates the area of rectangle
   * @param {*} dim1 the length of the rectangle
   * @param {*} dim2 the width of the rectangle
   * @returns {number} area of rectangle
   */
  function areaOfRectangle(dim1, dim2) {
    return dim1 * dim2;
  }

  /**
   * calulates the area of circle
   * @param {*} dim1 the radius of the circle
   * @returns {number} area of cricle
   */
  function areaOfcirCle(dim1) {
    return Math.PI * dim1 * dim1;
  }

  // exporting a file
  /**
   * description
   * @module fileName
   */

   /**
     * find sum of 2 numbers
    * @param {number} num1  first number
    * @param {number} num2  second number
    * @returns {number} sum of 2 numbers
    */

   export.sum = (num1, num2) {
      return num1 + num2;
    }

    // now import from other files
   const {sum} = require('./fileName')
  ```
