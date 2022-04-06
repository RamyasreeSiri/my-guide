# [⬅️](/myguides) TypeScript

## Quiz

* Why do developers want to use typescript
* Define `Inference`
* Define `literal types`
* Define `type annotation`
* Define `optional properties`
* Define `type guards`
* What is the difference between

  ```ts

    interface car {
      model: string
      chargeVoltage: number | undefined
    }
    
    // and

    interface car {
      model: string
      changeVoltage?: number
    }
  ```

  <details>
    <summary>▶️ Solution</summary>

    for the property which has a potential to have a value of undefined should be passed with value `undefined` and an optional property doesn't need to be passed.
  </details>

* Define `Index signature`
* Define `Tuple`
* List all types available in typescript

  <details>
    <summary>▶️ Solution</summary>
    1. string
    2. number
    3. boolean
    4. Function with argument types and return types
    5. Objects
    6. Arrays
    7. Tuples
    8. Union and Intersection types
  </details>

* What is typescripts type system?
  <details>
    <summary>▶️ Solution</summary>
    TypeScript’s type system is static(type check performed at compile type).
    TypeScript’s type system is structural(type checking involves the checking of structure or shape).
  </detials>
*

## Notes

1️⃣🚩Reference
[Course: React and TypeScript by Steve Kinney from Frontend Masters](https://frontendmasters.com/courses/react-typescript/)
[Course Website](https://stevekinney.github.io/react-and-typescript/)
[Course Code](https://stevekinney.github.io/react-and-typescript/)

### Why use TypeScript?

- Type checking at a compile time is way better than things crashing or worse behaving unexpectedly at run time.
- You get a better development experience because autocomplete knows more about what you're intending on doing.
- Large codebases stay more maintainable because you are able to put gaurdrails on how your code base can be used.

### Common Types

```tsx
// string, number, boolean
type CounterProps = {
  incident: string;
  count: number;
  enabled: boolean;
};

// array of strings
type GroceryListProps = {
  items: string[]; // array of strings
  status: "loading" | "error" | "success" // literal types
}

//
type Item = {
  id: string;
  title: string;
};

type ContrivedExampleComponentProps = {
  item: Item;
  items: Item[];
}

//
type ItemHash = {
  [key: string]: Item;
};

type Dictionary = {
  [key: number]: string;
}

```

### What is structural typing?

???

2️⃣🚩Reference
[Course: TypeScript Fundamentals, v3 by Mike North from Frontend Masters](https://frontendmasters.com/courses/typescript-v3/)
[Course Website](https://www.typescript-training.com/course/fundamentals-v3)
[Course Code](https://github.com/mike-north/ts-fundamentals-v3)

### Intro

**What is TypeScript?**
TypeScript is an [open source](https://github.com/microsoft/TypeScript),typed syntactic superset of JavaScript

**Why developers want types?**

- It allows you, as a code author, to leave more of your intent “on the page”
- It has the potential to move some kinds of errors from runtime to compile time
- It serves as the foundation for a great code authoring experience

### Using tsc and compiling TS code into JavaScript

- To complie `tsc --watch --preserveWatchOutput`

> tsc: typescript complier, complies to readable JS
> watch: Watch input files, watches for source changes, and rebuilds automatically
> preserveWatchOutput: Disable wiping the console in watch mode.

- compiler outputs `.js` and `.d.ts` files,
`.ts` files contain both type information and code that runs
`.js` files contain only code that runs
`.d.ts`, declaration files contain only type information

**Creating .d.ts files from .js filies**
```json
// tsconfig.json
{
  // Change this to match your project
  "include": ["src/**/*"],
  "compilerOptions": {
    // Tells TypeScript to read JS files, as
    // normally they are ignored as source files
    "allowJs": true,
    // Generate d.ts files
    "declaration": true,
    // This compiler run should
    // only output d.ts files
    "emitDeclarationOnly": true,
    // Types should go into this directory.
    // Removing this would place the .d.ts files
    // next to the .js files
    "outDir": "dist",
    // go to js file when using IDE functions like
    // "Go to Definition" in VSCode
    "declarationMap": true,
    // js files emitted can be run using node if they are "CommonJS" type modules
    "module": "CommonJS"
  }
}
```

> If you’d like to write tests for your .d.ts files, try [tsd](https://github.com/SamVerschueren/tsd).

### Variables and simple values

`let age = 6` on hover `let age: number`
 TypeScript is able to infer that age is a number, based on the fact that we’re initializing it with a value as we are declaring it.

#### Literal type
`const age = 6` on hover `const age: 6` here `age` will always be 6 in this program.

`let mostFlexibleType`, if no type is given then it ends up being an implicit `any`, `let mostFlexibleType: any `

`any` is the normal way JavaScript variables work, in that you could assign the above variable to a `number`, then later a `function`, then a `string`.

> TypeScript uses the syntax **:** type after an identifier as the type annotation, where type can be any valid type. Once an identifier is annotated with a type, it can be used as that type only.

#### Function arguments and return values

Type annotations are used to describe function arguments and its return value

`function add(a: number, b: number): number {return a + b}`

### Objects and arrays

*object types are defined by:*

The names of the properties that are (or may be) present
The types of those properties

```js

let car: {
  make: string
  model: string
  year: number
  chargeVoltage?: number // We can state that this property is optional using the ? operator
}

car = {
  make: "Toyota",
  model: "Corolla",
  year: 2002
}
```

#### Index Signature

```js
const phones = {
  home: { country: "+1", area: "211", number: "652-4515" },
  work: { country: "+1", area: "670", number: "752-5856" },
  fax: { country: "+1", area: "322", number: "525-4357" },
}

// Index signature
const phones: {
  [k: string]: {
    country: string
    area: string
    number: string
  }
} = {}
```

#### Array types

```js
const fileExtensions = ["js", "ts"];

const fileExtensions: string[]

const cars = [
  {
    make: "Toyota",
    model: "Corolla",
    year: 2002,
  },
]

const cars: {
    make: string;
    model: string;
    year: number;
}[]
```

#### Tuples

definition: multi-element, ordered data structure, where position of each item has some special meaning or convention.

```js
// here myCar type is implicitly decided as `let myCar: (string | number)[]`
let myCar = [2002, "Toyota", "Corolla"]
// which gives modal types as  `const model: string | number`
const [year, make, model] = myCar
```
using **tuple type** to define the type of tuple helps us to define with finite length and position of the value

```js
let myCar: [number, string, string] = [
  2002,
  "Toyota",
  "Corolla",
]

const [year, make, model] = myCar;
// here the types of above variables are considered as and any other type won't be considered
const year: number
const make: string
const model: string
```

*Limitation of tuple:* tuple length constraints is present on assignment but not around push and pop.

### Structural vs. Nominal Types

#### What is type checking?

Type-checking can be thought of as a task that attempts to evaluate the question of compatibility or type equivalence.

#### Static vs dynamic

> TypeScript's type system is static

**Static** type systems type checking is performed at compile time.
*examples*: `Java`, `C#`, `C++`

**Dynamic** type systems perform their "type equivalence" evaluation at run time.
*examples*: `JavaScript`, `Python`, `Ruby`, `Perl` and `PHP`

#### Nominal vs structural

> TypeScript type system is structural

- Nominal type systems are all about NAMES
- Structural type systems are all about STRUCTURE or SHAPE

[Reference](https://www.typescript-training.com/course/fundamentals-v3/05-structural-vs-nominal-types/#nominal-vs-structural)

#### Duck typing

“Duck typing” gets its name from the “duck test”.

“If it looks like a duck, swims like a duck, and quack like a duck, then it probably is a duck”.

In practice, this is very similar to structural typing, but “Duck typing” is usually used to describe dynamic type systems.

#### “Strong” vs. “Weak” types

“Duck typing” gets its name from the “duck test”.

“If it looks like a duck, swims like a duck, and quack like a duck, then it probably is a duck”.

In practice, this is very similar to structural typing, but “Duck typing” is usually used to describe dynamic type systems.

### Union and Intersection types

#### Union type

**Union Type**: works like OR `|` 

```ts
function flipCoin(): "heads" | "tails" {
  if (Math.random() > 0.5) return "heads"
  return "tails"
}

function maybeGetUserInfo():
  | ["error", Error]
  | ["success", { name: string; email: string }] {
  if (flipCoin() === "heads") {
    return [
      "success",
      { name: "Mike North", email: "mike@example.com" },
    ]
  } else {
    return [
      "error",
      new Error("The coin landed on TAILS :("),
    ]
  }
}

const outcome = flipCoin()
const outcome = maybeGetUserInfo()

const [first, second] = outcome
// const first: "error" | "success" - infered type
// const second: Error | {
//  name: string;
//  email: string;
// }
```

##### Narrowing with type guards

using Type guards we can access uncommon methods of the outcome
> Type guards are expressions, which when used with control flow statement, allow us to have a more specific type for a particular value.

```ts

if (second instanceof Error) {
  // In this branch of your code, second is an Error
  // second type is
  // const second: Error
  console.log(second.name)
} else {
  // In this branch of your code, second is the user info
  // second type here is
  // const second: {
  //     name: string;
  //     email: string;
  // }
  console.log(second.email)
}

```

##### [Discriminated](https://en.wikipedia.org/wiki/Tagged_union) Unions

The first and second positions of the tuple defined below are connected which is understood by TypeScript.

```ts
const outcome = maybeGetUserInfo()
if (outcome[0] === "error") {
  // In this branch of your code, second is an Error
  // outcome type infered by typescript as
  // const outcome: ["error", Error]
} else {
  // In this branch of your code, second is the user info
  // outcome type infered by typescript as
  // const outcome: ["success", {
  //   name: string;
  //   email: string;
  // }]
}
```

#### Intersection types

**Intersection types** in TypeScript can be described using the & (ampersand) operator.

```ts

function makeWeek(): Date & { end: Date } {
  //⬅ return type

  const start = new Date()
  const end = new Date(start.valueOf() + ONE_WEEK)

  return Object.assign(start, { end: end } // kind of Object.assign
}

const thisWeek = makeWeek()
thisWeek.toISOString()
// thisWeek type
// const thisWeek: Date & {
//     end: Date;
// }

thisWeek.end.toISOString()
// (property) end: Date - end type
```

> Note: It is far less common to use intersection types compared to union types

### Interfaces and Type Aliases

TypeScript uses 'interfaces' and 'type aliases' for centrally defining types and giving them useful and meaningful names

#### Type Aliases

> A name for any type

We can import and export them and give meaningful names and mostly use to define objects type

```ts
///////////////////////////////////////////////////////////
// @filename: types.ts
export type UserContactInfo = {
  name: string
  email: string
}
///////////////////////////////////////////////////////////
// @filename: utilities.ts
import { UserContactInfo } from "./types"

function printContactInfo(info: UserContactInfo) {
  console.log(info) // (parameter) info: UserContactInfo
  console.log(info.email) // (property) email: string
}

const painter = {
  name: "Robert Ross",
  email: "bross@pbs.org",
  favoriteColor: "Titanium White",
}

printContactInfo(painter) // totally fine
```

**limitations**:

- This is a rare occasion where we see type information on the right hand side of the assignment operator (=)
- We’re using TitleCase to format the alias’ name. This is a common convention
- we can only declare an alias of a given name once within a given scope. This is kind of like how a let or const variable declaration works

**Inheritence**:

You can create type aliases that combine existing types with new behavior by using Intersection (&) types.

```ts
type SpecialDate = Date & { getReason(): string }

const newYearsEve: SpecialDate = {
  ...new Date(),
  getReason: () => "Last day of the year",
}
newYearsEve.getReason()
```

#### Interfaces

> An interface is a way of defining an object type

```ts
interface UserInfo {
  name: string
  email: string
}

function printUserInfo(info: UserInfo) {
  info.name // (property) UserInfo.name: string
}
```

**Inheritence**:
`EXTENDS`:**heritage clause**, a sub-interface extends from a base-interface

```ts

interface Animal {
  isAlive(): boolean
}
interface Mammal extends Animal {
  getFurOrHairColor(): string
}
interface Dog extends Mammal {
  getBreed(): string
}
function careForDog(dog: Dog) {
  dog.getBreed()
  dog.getBreed()
  dog.getFurOrHairColor()
}
```
`IMPLEMENTS`: **second heritage clause**, A given class should produce instances that confirm to a given interface.

```ts
interface AnimalLike {
  eat(food): void
}

class Dog implements AnimalLike {
  bark() {
    return "woof"
  }
  eat(food) {
    consumeFood(food)
  }
}
```

While TypeScript (and JavaScript) does not support true [multiple inheritance](https://en.wikipedia.org/wiki/Multiple_inheritance) (extending from more than one base class), this implements keyword gives us the ability to validate, at compile time, that instances of a class conform to one or more “contracts” (types).
> Note that both extends and implements can be used together:

```ts
class LivingOrganism {
  isAlive() {
    return true
  }
}
interface AnimalLike {
  eat(food): void
}
interface CanBark {
  bark(): string
}

class Dog
  extends LivingOrganism
  implements AnimalLike, CanBark
{
  bark() {
    return "woof"
  }
  eat(food) {
    consumeFood(food)
  }
}
```

> A class can only implement an object type or intersection of object types with statically known members.
> *class can not implement the below type*
> `type CanBark =
  | number
  | {
      bark(): string
    }`
> For this reason, it is best to use **interfaces** for types that are used with the **implements** heritage clause.

#### Open interfaces

You can have multiple interface declarations in same scope which are merged to create single interface.

```ts
interface AnimalLike {
  isAlive(): boolean
}
function feed(animal: AnimalLike) {
  animal.eat // (method) AnimalLike.eat(food: any): void
  animal.isAlive // (method) AnimalLike.isAlive(): boolean
}

// SECOND DECLARATION OF THE SAME NAME
interface AnimalLike {
  eat(food): void
}
```
> **Choosing which to use**
>In many situations, either a `type` alias or an `interface` would be perfectly fine, however…

> If you need to define something other than an object type (e.g., use of the | union type operator), you must use a type alias
> If you need to define a type to use with the `implements` heritage term, it’s best to use an interface
> If you need to allow consumers of your types to *augment* them, you must use an interface.

#### Recursion

Recursive types, are self-referential, and are often used to describe infinitely nestable types

```ts
type NestedNumbers = number | NestedNumbers[]

const val: NestedNumbers = [3, 4, [5, 6, [7], 59], 221]
```

**Example using all the above concepts**:

```ts
type stringFunctionArgOne = (color: string) => string;

interface colorCodeCharacters {
  getCharacter: stringFunctionArgOne
}

interface colorCodePowers {
  getPower: stringFunctionArgOne
}

class colorCodePlanet {
  getPlanet: stringFunctionArgOne = printColor;
}

class powerRangers extends colorCodePlanet implements colorCodeCharacters, colorCodePowers {
  getCharacter = printColor;
  getPower = printColor;
  getName = printColor;
}

function isPowerRangers(name: any): name is powerRangers {
  return name instanceof powerRangers
}

interface blackClover extends colorCodePowers {
  getName: stringFunctionArgOne
  getTeam: stringFunctionArgOne
}

function newAnime(name: powerRangers | blackClover): string {
  if('getTeam' in name) {
    name.getTeam('blackClover-team');
  }
  if(name instanceof powerRangers) {
    name.getCharacter('powerRangers-character');
  }
  if(isPowerRangers(name)) {
    name.getCharacter('powerRangers-character2');
    name.getPlanet('powerRangers-planet')
  }
  return name.getName('name');
}

let pr = new powerRangers();

let bc: blackClover = {
  getName: printColor,
  getTeam: printColor,
  getPower: printColor
}

function printColor(color: string) {
  console.log(color);
  return color;
}
newAnime(pr);
newAnime(bc);
```

### Hack: Writing types for JSON values

[Exercise Link] (https://www.typescript-training.com/course/fundamentals-v3/08-exercise-json-types/)

### Functions

#### Call signatures

- Both type aliases and and interfaces offer the capability to describe [call signatures](https://www.typescriptlang.org/docs/handbook/2/functions.html#call-signatures)
```ts
// function type using `interface`
interface TwoNumberCalculation {
  (x: number, y: number): number
}
// function type using `type`
type TwoNumberCalc = (x: number, y: number) => number

const add: TwoNumberCalculation = (a, b) => a + b
const subtract: TwoNumberCalc = (x, y) => x - y

// 'Function type experssion' syntax
const addIndiv = (x: number, y: number): number => x+y;

function subtractIndiv(x: number, y: number): number {
  return x - y;
}
```

- Functions which doesn't have return has the return type as `void`

> The return value of a void function is intended to be ignored

#### Construct signatures

Construct signatures are similar to call signatures, except they describe what should happen with the new keyword.

```js
 interface DateConstructor {
  new (value: number): Date
}

let MyDateConstructor: DateConstructor = Date
const d = new MyDateConstructor()
// const d: Date
```

#### Function Overloads

- We define multiple function heads that serve as entry points to a single implementation

```ts

type FormSubmitHandler = (data: FormData) => void
type MessageHandler = (evt: MessageEvent) => void

function handleMainEvent(
  elem: HTMLFormElement,
  handler: FormSubmitHandler
)
function handleMainEvent(
  elem: HTMLIFrameElement,
  handler: MessageHandler
)
function handleMainEvent(
  elem: HTMLFormElement | HTMLIFrameElement,
  handler: FormSubmitHandler | MessageHandler
) {}

const myFrame = document.getElementsByTagName("iframe")[0]
// const myFrame: HTMLIFrameElement
const myForm = document.getElementsByTagName("form")[0]
// const myForm: HTMLFormElement

// function handleMainEvent(elem: HTMLIFrameElement, handler: MessageHandler): any (+1 overload)
handleMainEvent(myFrame, (val) => {
})
// function handleMainEvent(elem: HTMLFormElement, handler: FormSubmitHandler): any (+1 overload)
handleMainEvent(myForm, (val) => {
})
```

We have effectively created a linkage between the first and second arguments, which allows our callback’s argument type to change, based on the type of handleMainEvent’s first argument.
> “implementation” function signature must be general enough to include everything that’s possible through the exposed first and second function heads

#### `this` types

```ts
function myClickHandler(
  this: HTMLButtonElement,
  event: Event
) {
  this.disabled = true // (property) HTMLButtonElement.disabled: boolean
}
myClickHandler // function myClickHandler(this: HTMLButtonElement, event: Event): void

const myButton = document.getElementsByTagName("button")[0]
const boundHandler = myClickHandler.bind(myButton)
// const boundHandler: (event: Event) => void

boundHandler(new Event("click")) // bound version: ok
myClickHandler.call(myButton, new Event("click")) // also ok
```

> **Note** TypeScript understands that .bind, .call or .apply will result in the proper this being passed to the function as part of its invocation.

#### Function type best practices

- Explicitly define return types

### Classes in TypeScript

#### Class Fields

- We are stating the types of each class field
- We are stating the types of each constructor argument

```ts
class Car {
  // class fields
  make: string
  model: string
  year: number
  constructor(make: string, model: string, year: number) { // constructor argument
    this.make = make
    this.model = model
    this.year = year
  }
}

let sedan = new Car("Honda", "Accord", 2017)
sedan.activateTurnSignal("left") // not safe!
new Car(2017, "Honda", "Accord") // not safe!
```

#### Access Modifiers

- TypeScript provides three access modifier keywords, which can be used with class fields and methods, to describe who should be able to see and use them.

|keyword|who can access|
---|---|
|`public`|everyone (this is the default)|
|`protected`|the instance itself, and subclasses|
|`private`|only the instance itself|

```ts
class Human {
  public likes: number
  public color: string
  public hair: string
  protected gender = (g: string) => console.log(g);
  private genderOptions = ['male', 'female']

  constructor(likes: number, color: string, hair: string) {
    this.likes = likes;
    this.color = color;
    this.hair = hair;
  }

  protected createGender() {
    return this.gender(this.genderOptions[Math.floor((Math.random() * 2))])
  }
}

const yamuna = new Human(5, 'red', 'curly');
console.log(yamuna.genderOptions, yamuna.hair);

class Animal extends Human {
  constructor(likes: number, color: string, hair: string) {
    super(likes, color, hair)
  }

  public getGender() {
    this.createGender()
  }
}

const dog = new Animal(26, 'white', 'straight')
dog.getGender()
```
We see two examples of “limited exposure”

- Human can expose private functionality through defining its own protected functionality
- Animal can expose protected functionality through defining its own public functionality

> **Note:** Just like any other aspect of type information, access modifier keywords are only validated at compile time, with no real privacy or security benefits at runtime. This means that even if we mark something as `private`, if a user decides to set a breakpoint and inspect the code that’s executing at runtime, they’ll still be able to see everything.

**JS private `#fields`**

- As of TypeScript 3.8, TypeScript supports use of [ECMAScript private class fields](https://github.com/tc39/proposal-class-fields/). If you have trouble getting this to work in your codebase, make sure to double-check your Babel settings

```ts
class Car {
  public make: string
  public model: string
  #year: number

  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.#year = year
  }
}
const c = new Car("Honda", "Accord", 2017)
c.#year
// Property '#year' is not accessible outside class 'Car' because it has a private identifier.
```

**`readonly`**

- While not strictly an access modifier keyword (because it has nothing to do with visibility), TypeScript provides a readonly keyword that can be used with class fields.

```ts
class Car {
  public make: string
  public model: string
  public readonly year: number

  constructor(make: string, model: string, year: number) {
    this.make = make
    this.model = model
    this.year = year
  }

  updateYear() {
    this.year++
    // Cannot assign to 'year' because it is a read-only property.
  }
}
```

#### Param properties

Concise syntax for defining class properties

```ts
class Car {
  constructor(
    public make: string,
    public model: string,
    public year: number
  ) {}
}

const myCar = new Car("Honda", "Accord", 2017)
myCar.make
```

> The first argument passed to the constructor should be a string, and should be available within the scope of the constructor as make. This also creates a public class field on Car called make and pass it the value that was given to the constructor

```ts
class Base {}

class Car extends Base {
  foo = console.log("class field initializer")
  constructor(public make: string) {
    super()
    console.log("custom constructor stuff")
  }
}

const c = new Car("honda")
--------------is compiled to--------------------------
"use strict";
class Base {
}
class Car extends Base {
    constructor(make) {
        super();
        this.make = make;
        this.foo = console.log("class field initializer");
        console.log("custom constructor stuff");
    }
}
const c = new Car("honda");
```

- Note the following order of what ends up in the class constructor:

  1. super()
  2. param property initialization
  3. other class field initialization
  4. anything else that was in your constructor after super()

### Top and bottom types


### User-defined Type guards

### Handling nullish values

### Generics

### Hack: higher-order functions for dictionaries

### Wrap up