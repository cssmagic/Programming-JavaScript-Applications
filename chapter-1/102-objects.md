# [译] [102] 对象

## Objects

JavaScript has very rich Object Oriented (OO) features. The _JSON_ (JavaScript Object Notation) standard used in nearly all modern web applications for both communication and data persistence is a subset of JavaScript’s excellent object literal notation.

JavaScript uses a _prototypal inheritance_ model. Instead of classes, you have object prototypes. New objects automatically inherit methods and attributes of its parent object through the _prototype chain_. It’s possible to modify an object’s prototype at any time, making JavaScript a very flexible, dynamic language.

Evidence: It’s possible to mimic Java’s class-based OO and inheritance models in JavaScript virtually feature-for-feature, and in most cases, with less code. The reverse is not true.

Contrary to common belief, JavaScript supports features like encapsulation, polymorphism, multiple inheritance, composition, and much more.
