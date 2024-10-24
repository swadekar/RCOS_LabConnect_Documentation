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




