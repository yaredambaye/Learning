# DAY 1

## _Topics covered_

- Javascript refresher -- basic syntax and new es7 features
- Creating practice examples
- Wrap up to look over main points

## Javascript refresher

<br/>

### Topics

<br/>

### **Declaration**

**var** -> syntax used to declare a variable. This has global scope and it is bad practice to use it as it might cause unexpected errors and hard to identify bugs. <br/><br/>
**let** -> The main difference between let and var is that scope of a variable defined with let is limited to the block in which it is declared while variable declared with var has the global scope. So we can say that var is rather a keyword which defines a variable globally regardless of block scope.<br/><br/>
**const** -> used to declare something we assign once and never change. For good practice, this is what we need to use unless you need something that needs to variable. :100:

---

> **_NOTE:_**
>
> - var declarations are globally scoped or function scoped while let and const are block scoped.
> - var variables can be updated and re-declared within its scope; let variables can be updated but not re-declared; const variables can neither be updated nor re-declared.
> - They are all hoisted to the top of their scope. But while var variables are initialized with undefined, let and const variables are not initialized.
> - While var and let can be declared without being initialized, const must be initialized during declaration.

---

### **Arrow Functions**

This was the old way of creating functions

```javascript
function foo() {
  // code here
}
```

we now have an easier way called arrow function. This helps with shorter and cleaner code as well as solves **this** keyword problems. :beers:

```javascript
const foo = () => {
  // code here
};
```

there are a bunch of ways we can write the syntax

```javascript
const multiply = (x, y) => {
  return x * y;
}; // multiple parameters

const phraseSplitterEs6 = (phrase) => phrase.split(" "); // only one parameter. no need to use parenthesis in the argument

const logObj = () => {
  console.log(objString);
}; // no parameter means we need the parenthesis back
```

### **Exports and Imports**

we can export modules using default. This means it is the defualt export for the file.

if we have these two files

```javascript
//person.js

const person = { name: "abebe" };

export default person;
```

```javascript
//utility.js

export const clear = () => {
  console.log("cleared");
};

export const baseData = 10;
```

we can import them to another file using this syntax.

```javascript
//app.js

import person from "./person.js";
import prs from "./person.js"; // since this is the default export, we can name it what we like

import { baseData } from "./utility.js"; // we have to use curly braces to specify which import we are calling
import { clean } from "./utility.js";
```

### **Classes**

classes have properties and methods

```javascript
class Foo {
  property = "something"; // property of the class
  prop2 = 2;
  classMethod = () => {
    // this is a method and we are using an arrow function
    /*does something*/
  };
}
```

this is how we call a class

```javascript
const abebeFoo = new Foo();
abebeFoo.classMethod();
let smthng = abebeFoo.property;
```

classes can also extend from another class.

```javascript
class Animal {
  constructor() {
    this.noOfLegs = "4";
  }
  print = () => {
    console.log(this.noOfLegs);
  };
}

class Spider extends Animal {
  constructor() {
    super(); //always has te called when we extend another class
    this.noOfLegs = "8";
    this.name = "mitsy";
  }
  printName = () => {
    console.log(this.name);
  };
}
```

Class spider has access to all methods and properties that Animal has so we can do

```javascript
const spidey = new Spider();
spidey.printName(); // will print out mitsy
spidey.print(); // will print out 8 legs, because we over wrode what was originally there
```

with next generation javascript (ES7) we can actually take out the constructor call and improve the above class

```javascript

class Animal {
  noOfLegs = "4";

print = () => {
    console.log(this.noOfLegs);
  };
}

class Spider extends Animal {
    this.noOfLegs = "8";
    this.name = "mitsy";

printName = () => {
    console.log(this.name);
  };
}

```

### The spread operator

This is a very useful operator we can use to simplify our development flow.
some of the uses are

- Copying an array
- Concatenating or combining arrays
- Using Math functions
- Using an array as arguments
- Adding an item to a list
- Adding to state in React
- Combining objects
- Converting NodeList to an array

#### How to use it

**spread operator** => (...) using these three dots we can

- split up array or object properties and assign them to new ones

  ```javascript
  const arr = [1, 2, 3, 4, 5];
  const newArr = [...arr, 6];

  console.log(arr); //prints [1,2,3,4,5]
  console.log(newArr); //prints [1,2,3,4,5,6]
  ```

- copy an array

  ```javascript
  const arr = [1, 2, 3, 4, 5];
  const newArr = [...arr];

  console.log(arr); //prints [1,2,3,4,5]
  console.log(newArr); //prints [1,2,3,4,5]
  ```

- concatinate an array

  ```javascript
  const arr = [1, 2, 3, 4, 5];
  const arr2 = [6, 7, 8, 9, 10];
  const combined = [...arr, ...arr2];
  console.log(combined); //prints [1,2,3,4,5,6,7,8,9,10]
  ```

- Math functions
  the built-in functions Math.min() and Math.max(), which both expect a list of arguments, not an array.
  ```javascript
  const numbers = [37, -17, 7, 0];
  console.log(Math.min(numbers)); // NaN
  console.log(Math.min(...numbers)); // -17
  console.log(Math.max(...numbers)); // 37
  ```
