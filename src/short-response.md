# Section 2 — Short Response

Write your responses directly in this file. Follow markdown formatting guidelines. Check the rubric.md file to see how your short responses will be graded. 

As a quick guide, check the following before submitting:
- [] Answered all parts of every question
- [] No typos or grammar mistakes (use grammarly!)
- [] Accurately uses relevant technical terminology
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Responses are concise and easy to comprehend

---

## Question 1

In your own words, explain what does _encapsulation_ refer to? Why is this concept beneficial when programming? 

Provide a code snippet to illustrate _encapsulation_.

## Response 1

_Encapsulation_ refers to data being **bundled together into one object** instead of separating data into different functions. This concept is beneficial for programming because it allows for a **separation of concerns**, helps create a **consistent and predictable algorithm**, and allows the programmer to use **private, public, and static methods** according to the way the data has been determined to be accessed. An example of _encapsulation_ would be the following:

``` js
class Quiz {
  static allQuizTypes = [];

  constructor(quizType, answerChoices) {
    this.quizType = quizType;
    this.answerChoices = answerChoices;
    Quiz.allQuizTypes.push(quizType);
  }
}
```

In this example, every time the programmer creates a quiz, the `Quiz` class adds the `quizType` to `allQuizTypes` which then allows the user to see all the quiz types and be able to choose a quiz to play through invoking `Quiz.allQuizTypes()`. This demonstrates _encapsulation_ as **all quiz data is bundled together** into the `Quiz` class which can then have methods that allow the programmer to create quiz features such as print all quiz types, randomize the quiz's answer choices, when the quiz ends they can print a message for the user regarding the quiz they played, and so on.

## Question 2

Explain what the `this` keyword is. Why is the `this` keyword useful?

In the code snippet below, what does `this` refer to?

```js
class Counter {
	constructor() {
		this.count = 0;
	}
  increment() {
    this.count++;
  }
}

const counterA = new Counter();
const counterB = new Counter();

counterA.increment();
counterA.increment();
counterA.increment();

counterB.increment();

console.log(counterA.count);
console.log(counterB.count);
```

## Response 2

The `this` keyword refers to the **object** that invokes the **method where the `this` keyword lives in**. `this` is useful because it allows the programmer to **refer to a class's instance** and access each **instance's properties and methods**. In the example above, the `this` keyword refers to the class `Counter`, which accesses the class's `count` property for each instance of `Counter`.


## Question 3

In your own words, explain what **polymorphism** means in OOP. Provide an example in code that demonstrates polymorphism.

## Response 3

_Polymorphism_ is a term used to describe when **methods or objects with the same name take on different forms**. The program executes a method **based on its place in the prototype chain**, meaning that even though 2 methods can have the same name, when invoked the program will make a _distinction between the methods_. The following is an example of polymorphism:

```js
class Dog {
  speak () {
    console.log(`Bark bark!`);
  }
}

class Robot {
  speak () {
    console.log(`hello...`);
  }
}
```

In the example above, the `speak` method demonstrates an example of polymorphism. When `Dog.speak()` is invoked, the console prints `Bark bark!`, when `Robot.speak()` is invoked, the console prints `hello...`. Even though both `Dog` and `Robot` use the same method name `speak`, **the program would still make a distinction between both classes**.

## Question 4

You're building a game where players can raise different digital pets: Cats, Dogs, and Birds. All pets have have a `name`, `energy` level, and `happiness` level and can all `sleep`. Cats have the ability to `hunt`, dogs have the ability to `chase`, and birds have the ability to `fly`.

**Part A:** Describe in words how you would use inheritance to organize these classes.

**Part B:** Explain one advantage of using inheritance here instead of creating three completely separate classes.

## Response 4
A. I would use _inheritance_ to organize these classes by making a `Pet` class. In this `Pet` class I would have `name`, `energy` level, and `happiness` level be public properties in the constructor and then have a `sleep` method that applies to all the pets. Then in each individual pet class I would inherit the `Pet` constructor properties and automatically inherit the `sleep` method. Then, I would only have to include each pet's individual abilities as a method. Here is an example:

```js
class Pet {
  constructor (name, energy, happiness) {
    this.name = name
    this.energy = energy
    this.happiness = happiness
  }
  sleep(){
    console.log(`${this.name} is sleeping`)
  }
}

class Cat extends Pet {
  constructor(name, energy, happiness) {
    super(name, energy, happiness)
  }
  hunt(){
    console.log(`${this.name} is on an active hunt for fish`)
  }
}
class Dog extends Pet {
  constructor(name, energy, happiness) {
    super(name, energy, happiness)
  }
  chase(){
    console.log(`${this.name} is chasing the squirrel`)
  }
}
class Bird extends Pet {
  constructor(name, energy, happiness) {
    super(name, energy, happiness)
  }
  fly(){
    console.log(`${this.name} has taken to the skies`)
  }
}
```

B. One advantage of using _inheritance_ is that I would avoid **repetitive code** and maintain a **consistent and predictable algorithm**. I wouldn't have to include a `sleep` method 3 times throughout the separate pet classes, instead I would only include it in the `Pet` class and have all other classes inherit the method.