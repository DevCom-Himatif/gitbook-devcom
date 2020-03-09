---
description: 2 Maret 2020
---

# TypeScript Crashcourse

### Basic Typing

There are 3 basic types in TypeScript

```typescript
var isDone: boolean = false;
let lines: number = 69;
const name: string = 'Jajang';
```

But **you can omit** the type annotation if the variables are **derived** from explicit literals

```typescript
var isDone = false;
let lines = 69;
const name = 'Jajang';
```

When it's impossible to know, there is the `any` type

```typescript
let notSure: any = 4;
notSure = 'maybe a string instead';
notSure = false;    // okay, definitely a boolean
```

Use `const` keyword for _constants_

```typescript
const numLivesForCat = 9;
numLivesForCat = 1; // Error
```

For _collections_, there are typed arrays and generic arrays

```typescript
let list: number[] = [1, 2, 3];

// Or, using the generic array type
let list: Array<number> = [1, 2, 3];
```

For _enumerations_

```typescript
enum Color { Red, Yellow, Green };
let c: Color = Color.Green;

if (c === Color.Green) {
    console.log('Lets go!');
}
```

Lastly, `void` is used in the special case of a function returning nothing.

```typescript
function bigHorribleAlert(): void {
  alert('I'm a little annoying box!');
}
```

### Functions

Functions are first class citizens, support the lambda 'fat arrow' syntax and use type inference.

The following are equivalent, the same signature will be inferred by the compiler, and same JavaScript will be emitted

Regular function

```text
// Function Declaration
function f1(i: number): number {
return i * i;
}

// Function Expression let f1 = function (i: number): number { return i * i; }
```

Return type inferred

```text
```
let f2 = function (i: number) {
  return i * i;
}
```

'Fat arrow' syntax

```typescript
let f3 = (i: number): number => {
return i * i;
}
```

'Fat arrow' syntax with return type inferred

```typescript
let f4 = (i: number) => { return i * i; }
```

'Fat arrow' syntax with return type inferred, _braceless_ means no return keyword needed.

```typescript
let f5 = (i: number) => i * i;
```

### `var`, `let`, and `const`

Declaring a variable using the above keywords:

* Both type and initial value.

  ```typescript
  var width:number = 100;
  let height:number = 200;
  const key:string = 'abc123';
  ```

* Without type, but with an initial value.

  ```typescript
  var width = 100;
  let height = 200;
  const key = 'abc123';
  ```

* Only the type.

  ```typescript
  var width: number;
  let height: number;
  // const does not support without initial value
  ```

* Without type and initial value.

  ```typescript
  var width;
  let height;
  // const does not support without initial value
  ```

### Variable Scoping

```cpp
void leFn() {
    std::string umurWawan = 25;
    std::cout << umurWawan; // ok
}

void leOtherFn() {
    std::cout << umurWawan; // WaWAn saHA ANyI...
}
```

#### `var` is **Function** Scoped

```typescript
function someFn() {   

  if (true) {        

    // defined locally
    // its scope ends where curly braces ends
    var local = 1000;

    console.log(local);   //ok

  }

  console.log(local);     //ok

  function nested() {         
    console.log(local);   //ok
  }

}

console.log(local);       //error
```

#### `let` and `const` are **Block** Scoped

```typescript
function someFn() {   

  if (true) {        

    // defined locally
    // its scope ends where curly braces ends
    let local = 1000;

    console.log(local);   // ok
  }

  console.log(local);     //error

  function nested() {         
    console.log(local);   //error
  }

}

console.log(local);       //error
```

### Interfaces

Interfaces are **structural**, anything that has the properties is compliant with the interface.

```typescript
interface Person {
  name: string;

  // Optional properties, marked with a '?'
  age?: number;

  // And of course functions
  move(): void;
}
```

Object that implements the `Person` interface can be treated as a `Person` since it has the name and move properties

```typescript
let p: Person = {
  name: 'Bobby',
  move: () => { }
};

let validPerson: Person = {
  name: 'Bobby',
  age: 42,    // optional property
  move: () => { }
};
```

Object below is **not** a person because age is not a number and there is no `move` function.

```typescript
let invalidPerson: Person = {
  name: 'Bobby',
  age: true
};
```

Interfaces can also describe a function type

```typescript
interface SearchFunc {
  (source: string, subString: string): boolean;
}
```

Only the **parameters' types** are important, names are not important.

```typescript
let mySearch: SearchFunc;

mySearch = function (src: string, sub: string) {
  return src.search(sub) != -1;
}
```

### Classes

Class members are public by default

```typescript
class Point {
  // Properties
  x: number;

  /* Constructor - the public/private keywords 
   * in this context will generate the boiler 
   * plate code for the property and the 
   * initialization in the constructor.
   *
   * In this example, 
   * 'y' will be defined just like 'x' is,
   * but with less code
   * 
   * Default values are also supported
   */

  constructor(x: number, public y: number = 0) {
    this.x = x;
  }

  // Functions
  dist() {
    return Math.sqrt(this.x * this.x + this.y * this.y);
  }

  // Static members
  static origin = new Point(0, 0);
}
```

```typescript
let p1 = new Point(10, 20);
let p2 = new Point(25);   //y will be 0
```

Classes can be explicitly marked as implementing an interface. Any missing properties will then cause an error at compile-time.

```typescript
class PointPerson implements Person {
  name: string;
  move() {}
}
```

Class inheritance

```typescript
class Point3D extends Point {
  constructor(x: number, y: number, public z: number = 0) {
    // Explicit call to the super class constructor 
    // is mandatory
    super(x, y);
  }

  // Override
  dist() {
    let d = super.dist();
    return Math.sqrt(d() * d() + this.z * this.z);
  }
}
```

### Generics

Classes

```typescript
class Tuple<T1, T2> {
  constructor(public item1: T1, public item2: T2) {}
}
```

Interfaces

```typescript
interface Pair<T> {
  item1: T;
  item2: T;
}
```

And functions

```typescript
let pairToTuple = function <T>(p: Pair<T>) {
  return new Tuple(p.item1, p.item2);
};
```

```typescript
let tuple = pairToTuple({
  item1: 'hello',
  item2: 'world'
});
```

### Template strings

Template Strings: strings that use backticks \(\`\).

String Interpolation with Template Strings

```typescript
let name = 'Tyrone';
let greeting = `Hi ${name}, how are you?`
```

Multiline Strings with Template Strings

```typescript
let multiline = `This is an example
of a multiline string`;
```

### Iterators

* `for..of` statement. Iterate over the list of **values** on the object being iterated.

```text
let arrayOfAnyType = [1, 'string', false];
for (const val of arrayOfAnyType) { console.log(val); // 1, 'string', false }

let list = [4, 5, 6];
for (const i of list) {
  console.log(i); // 4, 5, 6
}
```

let arrayOfAnyType = \[1, 'string', false\];

for \(const val of arrayOfAnyType\) { console.log\(val\); // 1, 'string', false }

let list = \[4, 5, 6\];

for \(const i of list\) { console.log\(i\); // 4, 5, 6 }

```text
* `for..in` statement. Iterate over the list of **keys** on the object being iterated.
```ts
for (const i in list) {
   console.log(i);    // 0, 1, 2
}
```

* Higher order functions

  \`\`\`ts

  let arrayOfAnyType = \[1, 'string', false\];

arrayOfAnyType.forEach\(i =&gt; console.log\(i\)\); // 1, 'string', false

const names = \['Ujang', 'Supardi', 'Wawan'\] names.forEach\(\(name: string\) =&gt; { console.log\(`Halo, selamat datang ${name}`\); }\)

```text
---

## More Types

* Union Types (`|`)
```ts
let code: string | number;
code = 123;     // ok
code = 'ABC';   // ok
code = false;   // compiler error
```

* Intersection Types \(`&`\)

  \`\`\`ts

  interface Animal {

  kind: string;

  }

interface Person { firstName: string; lastName: string; age: number; }

interface Employee { employeeCode: string; }

let employee: Animal & Person & Employee = { kind: 'human', firstName: 'Jane', lastName: 'Smith', age: 20, employeeCode: '123' }

\`\`\`

