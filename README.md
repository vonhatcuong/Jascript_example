#JavaScript 7 Syntax and Operators.

1. First, you will learn all about the switch statement and the difference between for/in and for/of.
```JavaScript
   function simpleSwitch() {
      let productId = 2;

      switch (productId) {
        case 1:
          console.log("HL Road Frame - Black, 58");
          break;
        case 2:
          console.log("Sport-100 Helmet, Red");
          break;
        case 3:
          console.log("Mountain Bike Socks, M");
          break;
        default:
          console.log("Unknown product");
          break;
      }
    }
```

2. Next, you will discover the various math, comparison, and logical operators, in addition to handling exceptions and determining the data type of variables.
```JavaScript
    let _products = [
      {
        "productID": 680,
        "name": "HL Road Frame - Black, 58",
        "productNumber": "FR-R92B-58",
        "color": "Black",
        "standardCost": 1059.31,
        "listPrice": 1431.50
      },
      {
        "productID": 707,
        "name": "Sport-100 Helmet, Red",
        "productNumber": "HL-U509-R",
        "color": "Red",
        "standardCost": 13.08,
        "listPrice": 34.99
      },
      {
        "productID": 709,
        "name": "Mountain Bike Socks, M",
        "productNumber": "SO-B909-M",
        "color": "White",
        "standardCost": 3.3963,
        "listPrice": 9.50
      }
    ];

    // Using a for/in loop
    function forinSample() {
      let product = {
        "productID": 680,
        "name": "HL Road Frame - Black, 58",
        "productNumber": "FR-R92B-58",
        "color": "Black",
        "standardCost": 1059.31,
        "listPrice": 1431.50,
        calculateGrossProfit: function () {
          return this.listPrice - this.standardCost;
        }
      };

      for (const key in product) {
        console.log("'" + key + "'=" + product[key]);
      }
    }

    // Using a for/of loop
    function forofSample() {
      for (const item of _products) {
        console.log(JSON.stringify(item));
      }
    }

    // Looping over a string
    function loopStringSample() {
      let productName = "HL Road Frame - Black, 58";
      let letters = "";

      for (const char of productName) {
        letters += char;
      }
      console.log(letters);
    }

    // Use the break statement
    function breakSample() {
      for (const item of _products) {
        if (item.standardCost < 20) {
          break;
        }
        console.log(JSON.stringify(item));
      }
    }

    // Use the continue statement
    function continueSample() {
      for (const item of _products) {
        if (item.standardCost > 1000) {
          continue;
        }
        console.log(JSON.stringify(item));
      }
    }

    // Use of a label.
    // NOTE: I don't recommend use of labels as this leads to spaghetti code
    function labelSample() {
      even:
      for (let index = 1; index <= 10; index++) {
        if (index % 2 == 1) {
          continue even;
        }
        console.log(index);
      }
    }
```
3. Finally, you will explore the 'this' keyword and the spread operator. When you are finished with this course, you will have gained the skills and knowledge of JavaScript syntax and operators needed to propel your JavaScript applications to the next level.
```javascript
    console.log("Begin: global scope sample");
    console.log(this.toString());
    console.log("this === window = " + (this === window).toString());
    console.log("End: global scope sample");

    // Function scope - 'this' is mapped to global/window object
    //                  Uncomment 'use strict' above to show how it affects this function
    function functionScope() {      
      console.log(this.toString());
      console.log("this === window = " + (this === window).toString());
    }
	
    // Pass 'this' to function from event handler
    function eventHandler(ctl) {
      console.log(ctl.toString());
    }

    // Object literal
    function objectLiteral() {
      let product = {
        "productID": 680,
        "name": "HL Road Frame - Black, 58",
        "standardCost": 1059.31,
        "listPrice": 1431.50,
        grossProfit: function () {
          return (this.listPrice - this.standardCost)
            .toLocaleString('en-US', {
              style: 'currency', currency: 'USD'
            });
        }
      };

      console.log(product.grossProfit());
    }

    function callAndApply() {
      let product = {
        "productID": 680,
        "name": "HL Road Frame - Black, 58",
        "standardCost": 1059.31,
        "listPrice": 1431.50,
        grossProfit: function () {
          return (this.listPrice - this.standardCost)
            .toLocaleString("en-US", {
              "style": "currency", "currency": "USD"
            });
        }
      };

      let prod2 = {
        "standardCost": 500,
        "listPrice": 850
      }

      // Call using reference to 'product' properties
      console.log(product.grossProfit.call(product));
      // Call using reference to 'prod2' properties
      console.log(product.grossProfit.call(prod2));
      console.log("");
      console.log(product.grossProfit.apply(product));
      console.log(product.grossProfit.apply(prod2));
    }

    function constructorFunctions() {
      let prod1 = new Product(680, "HL Road Frame - Black, 58", 1059.31, 1431.50);
      let prod2 = new Product(707, "Sport-100 Helmet, Red", 13.08, 34.99);

      console.log(prod1.grossProfit());
      console.log(prod2.grossProfit());
    }

    function Product(id, name, cost, price) {
      this.productID = id;
      this.name = name;
      this.standardCost = cost;
      this.listPrice = price;

      this.grossProfit = function () {
        return (this.listPrice - this.standardCost)
            .toLocaleString("en-US", {
              "style": "currency", "currency": "USD"
            });
      }
    }
```
## References from  [pluralsight.com](https://app.pluralsight.com/library/courses/javascript-syntax-operators).