# TypeScript Learning Notes

Welcome to my TypeScript learning folder! Here, I document key concepts, code snippets, and resources as I explore TypeScript. Each section covers different aspects of the language, and I'll update this as I progress.

## Table of Contents
- [Introduction to TypeScript](#introduction-to-typescript)
- [Setup](#setup)
- [Basic Types](#basic-types)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Classes](#classes)
- [Generics](#generics)
- [Advanced Topics](#advanced-topics)
- [Resources](#resources)

## Introduction to TypeScript
TypeScript is a superset of JavaScript that adds static typing. It enhances code quality and maintainability.

## Setup
To set up TypeScript on your local machine:
1. **Install Node.js** from [nodejs.org](https://nodejs.org/).
2. **Install TypeScript** globally using npm:
   ```bash
   npm install -g typescript

   mkdir my-typescript-project
cd my-typescript-project
tsc --init

Basic Types
TypeScript includes several basic types:

string
number
boolean
array
tuple
enum
any

Examples:
let age: number = 30;
let name: string = "Siddhi";
let isStudent: boolean = true;

Functions
Functions can have typed parameters and return types.
function greet(name: string): string {
    return `Hello, ${name}`;
}

Interfaces
Interfaces define the structure of objects.
interface Person {
    name: string;
    age: number;
}

const user: Person = {
    name: "Siddhi",
    age: 25
};


Classes
TypeScript supports object-oriented programming with classes.

class Animal {
    constructor(public name: string) {}

    speak() {
        console.log(`${this.name} makes a noise.`);
    }
}

const dog = new Animal("Dog");
dog.speak();


Generics
Generics allow for reusable components.
function identity<T>(arg: T): T {
    return arg;
}

let output = identity<string>("Hello");

### 1. Type Assertion
Type assertion allows you to override the inferred type of a variable. This is useful when you know more about the type of a variable than TypeScript does.

#### Example
```typescript
let someValue: unknown = "this is a string";
let strLength: number = (someValue as string).length; // Using 'as' syntax


2. Union Types
Union types allow a variable to be one of several types. This is useful when a value can be of different types.

function displayId(id: number | string) {
    console.log(`Your ID is: ${id}`);
}

displayId(101); // Works
displayId("202A"); // Also works


3. Intersection Types
Intersection types allow you to combine multiple types into one. This is helpful when you want to merge properties of different types.

interface User {
    id: number;
    name: string;
}

interface Admin {
    role: string;
}

type AdminUser = User & Admin;

const admin: AdminUser = {
    id: 1,
    name: "Alice",
    role: "Administrator"
};


4. Type Guards
Type guards are techniques used to narrow down the type of a variable within a conditional block. This can enhance type safety.

function isString(value: unknown): value is string {
    return typeof value === 'string';
}

const input: unknown = "Hello, TypeScript!";
if (isString(input)) {
    console.log(input.toUpperCase()); // Safe to call string methods
}


5. Decorators
Decorators are a special kind of declaration that can be attached to a class, method, accessor, property, or parameter. They can be used to modify or enhance behavior.

function Log(target: any, propertyName: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;
    descriptor.value = function (...args: any[]) {
        console.log(`Calling ${propertyName} with`, args);
        return originalMethod.apply(this, args);
    };
}

class MathOperations {
    @Log
    add(a: number, b: number) {
        return a + b;
    }
}

const math = new MathOperations();
math.add(5, 10); // Logs: "Calling add with" [5, 10]


6. Mapped Types
Mapped types allow you to create new types by transforming properties of an existing type.

type Person = {
    name: string;
    age: number;
};

type ReadOnly<T> = {
    readonly [K in keyof T]: T[K];
};

const user: ReadOnly<Person> = {
    name: "Siddhi",
    age: 25
};

// user.age = 26; // Error: Cannot assign to 'age' because it is a read-only property.

7. Conditional Types
Conditional types enable type definitions that depend on a condition. This can be useful for creating more flexible types.

type IsString<T> = T extends string ? "Yes" : "No";

type Test1 = IsString<string>; // "Yes"
type Test2 = IsString<number>; // "No"


8. Utility Types
TypeScript provides several utility types that can help manipulate types easily.

Partial: Makes all properties of a type optional.
Required: Makes all properties of a type required.
Readonly: Makes all properties of a type read-only.

interface Task {
    id: number;
    title: string;
}

const partialTask: Partial<Task> = {
    title: "Learn TypeScript" // 'id' is optional here
};

const readOnlyTask: Readonly<Task> = {
    id: 1,
    title: "Immutable Task"
};

// readOnlyTask.title = "New Title"; // Error: Cannot assign to 'title' because it is a read-only property.


9. Advanced Generics
Generics can be more advanced with constraints and default types, allowing for more flexible and reusable components.

function merge<T extends object, U extends object>(objA: T, objB: U) {
    return Object.assign({}, objA, objB);
}

const merged = merge({ name: "Siddhi" }, { age: 25 });
// Result: { name: "Siddhi", age: 25 }

10. Namespaces
Namespaces provide a way to organize code and prevent naming conflicts, especially in larger projects.

namespace MathUtils {
    export function add(a: number, b: number) {
        return a + b;
    }
    export function subtract(a: number, b: number) {
        return a - b;
    }
}

const sum = MathUtils.add(5, 10);
const difference = MathUtils.subtract(10, 5);






