---
layout: post
title:      "This and That...but mainly This"
date:       2020-12-19 18:50:27 +0000
permalink:  this_and_that_but_mainly_this
---


`this` is an important keyword in Javascript. In a nutshell, it's very similar to `self` in Ruby. 

What `this` refers to depends on the execution context from where it's called. 

- By itself, `this` will refer to the **global object**
- Inside an object method, `this` refers to the **instance of the object**
- Inside a function, `this` refers to the **global object**
- Inside an event, `this` refers to the **element triggering the event**

If you type `this` in your browser's console, you would get something returned as such:

```
Window {window: Window, self: Window, document: document, name: "", location: Location, …}
```

Since `this` is being called on its own, it is referencing the **global object** which is the browser window in this case.

When you look at it inside an object method, you can see its similarity with Ruby's `self` interaction with class and instance methods.

```
class Dog {

    constructor(name, breed) {
        this.name = name;
        this.breed = breed;
    }

}

let Dog = new Dog('Bogo', 'Golden Retriever')

// => Dog {name: "Bogo", breed: "Golden Retriever"}
```

In the code snippet above, the constructor method for the `Dog` class uses `this` to reference the newly created instance of a `Dog` class/object and assigns the appropriate values to it.

Important understanding of `this` and how it works with the execution context of your code will help create cleaner code and further encapsulate your code through Object Oriented Programming. 
