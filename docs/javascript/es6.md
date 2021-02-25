# ES6 for begginers

This cheatsheet is a copy/paste from [this article](https://medium.com/the-react-native-log/a-brief-overview-of-es6-for-react-native-developers-15e7c68315da). Praise to Spencer Carli for writing this wonderful wrap up.

## Variables
Since the advent of JavaScript we’ve had `var`. But now we have `var`, `let`, and `const`. They're all valid but what's the difference?

`let`: Very similar to var but the scoping is different. var is function scoped (available and can be modified anywhere within a function) whereas let is block scoped, meaning it's available only within that block of code. I pretty much always use let in place of var now (honestly I can't remember the last time I used var).

`const`: Same scoping (block) as let but you can't change the value of it, for example:

```javascript
const name = 'Spencer';
name = 'Johnny' // Can't do this
```

However (and this is something that I was confused about at first) you can modify it if it’s of a type object or array, for example:

```javascript
const info = {
  name: 'Spencer',
  company: 'Handlebar Labs',
};
info.job = 'Teaching'; // This is perfectly valid
const roles = ['Student', 'Teacher'];
roles.push('Developer'); // Good to go!
```

Want more info?

* [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)
* [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)

## Arrow Functions
### Syntax
There’s now a new way to declare functions in JavaScript called arrow functions, and you’ll see these a lot when working with React or React Native. The primary difference between standard/old functions and arrow functions is what `this` is bound to, so sometimes you'll want/need to use `function`. Creating an arrow function is simple

```javascript
const greet = (name) => {
  return 'Hello, ' + name + '!';
};
greet('Spencer'); // Hello, Spencer!
```
[Learn more about arrow function syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#syntax)

### Formatting Arguments
With arrow functions you can format arrow functions in a few different ways, all of which are commonly used. These are the three rules I’ve commited to memory.

#### No arguments = parenthesis required
```javascript
const greet = () => {
  return 'Hi!';
};
```
#### One argument = parenthesis optional
```javascript
const greet = (name) => {
  return 'Hello, ' + name + '!';
};
const greet = name => {
  return 'Hello, ' + name + '!';
};
```
#### Two or more arguments = parenthesis required
```javascript
const greet = (name, company) => {
  return 'Hello, ' + name + '!' + 'How is ' + company + '?';
};
```
[Learn more about formatting arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#basic_syntax)

### Default Arguments
This is one of my favorites — an extremely simple way to set default arguments for your functions by simply assigning them to a value when naming the argument. If the argument is passed it will use the argument you pass, otherwise it will fall back to the default.
```javascript
const greet = (name = 'Friend') => {
  return 'Hello, ' + name + '!';
};
greet(); // Hello, Friend!
greet('Spencer'); // Hello, Spencer!
```
[Learn more about default arguments](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#advanced_syntax)

### Implicit Return
Have a simple function and sick of writing curly braces and returns? Fret no more! You’re now able to implicitly return from a function, like so
```javascript
const greet = (name) => 'Hello, ' + name + '!';
greet('Spencer'); // Hello, Spencer!
```
Mmm saved keystrokes

It gets better though! Say you want to return an object from a function, you can do so like so (you’ll often see this when working with Redux)
```javascript
const getInfo = () => ({
  name: 'Spencer',
  company: 'Handlebar Labs',
  job: 'Teaching',
});
getInfo(); // { name: 'Spencer', company: 'Handlebar Labs', job: 'Teaching' }
```
(notice the parenthesis wrapping the object)

And finally you’re also able to return a component in a very similar way as the object, let me demonstrate
```javascript
const Greeting = ({ name }) => (
  <View>
    <Text>Hello, {name}!</Text>
  </View>
);
```
Again we’re wrapping the component with parenthesis and we don’t have to do any returns.

[Learn more about implicit returns](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#basic_syntax)

## Objects
We’ve now got a few very convenient tools (that previously would have required an external library) that make working with Objects in JavaScript easier.

### Destructuring
Destructuring allows us to “destructure”, or break down, an object so that we can more easily access the information we care about. Let’s say we want to access some data on an object, in the past we would have had to do the following
```javascript
const info = {
  name: 'Spencer',
  company: 'Handlebar Labs',
  location: {
    city: 'Nashville',
    state: 'Tennessee',
  },
};
const name = info.name;
const city = info.location.city;
const state = info.location.state;
```
That’s fine but now we’re able to save a bit of time defining the variables that access the info we care about. When you’re passing props around a React Native application it’s common to have some nested data and, as we see with city and state, we end up writing a lot of the same code. You’re able to destructure that object to more easily access data.
```javascript
const info = {
  name: 'Spencer',
  company: 'Handlebar Labs',
  location: {
    city: 'Nashville',
    state: 'Tennessee',
  },
};
const { name, location } = info;
const { city, state } = location;
// name is Spencer
// city is Nashville
// state is Tennessee
```
You’ll often see this when accessing information from props, like this:
```javascript
const Info = ({ name, location }) => (
  <View>
    <Text>{name} lives in {location.city}, {location.state}</Text>
  </View>
);
```

[Learn more about object destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#object_destructuring)

### Spread
Object spreading allows us to copy information from one object to another. It’s a practice you’ll often see when using Redux because of the need for pure functions. Let’s say we have multiple people who work at Handlebar Labs and they’ve all got some of the same basic information. To save time we’ll copy that information from the “template” to an individual’s information.
```javascript
const handlebarLabsInfo = {
  company: 'Handlebar Labs',
  location: {
    city: 'Nashville',
    state: 'Tennessee',
  },
};
const spencerInfo = {
  ...handlebarLabsInfo,
  name: 'Spencer',
}
console.log(spencerInfo); // { name: 'Spencer', company: 'Handlebar Labs', location: { city: 'Nashville', state: 'Tennessee' } }
```
[Learn more about object spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#spread_in_object_literals)

## Strings
### Template Literals
Another personal favorite of mine. Notice how earlier, or in any of your older code/tutorials, you see `'Hello, ' + name + '!' + 'How is ' + company + '?'`? Those + signs can be a pain to write and I know personally I would always forget a space, thus causing the formatting to look off. Template literals make it easier for us because we can much more naturally write strings with dynamic content.

By using back ticks (\`\`) to defined the string we can then pass variables in with `${}`. Let me just show you...
```javascript
const greet = (name, company) => {
  // return 'Hello, ' + name + '!' + 'How is ' + company + '?';
  return `Hello, ${name}! How is ${company}?`;
};
```
So much better 😄

[Learn more about template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)

## Modules
For people first jumping over to React Native this one can be confusing. You’re probably used to seeing
```javascript
exports.greet = (name) => 'Hello, ' + name + '!';
// OR
module.exports = (name) => 'Hello, ' + name + '!';
```
and likewise to actually use that code:
```javascript
const formalities = require('./formalities');
formalities.greet();
const greet = require('./formalities');
greet();
```
We’ve now got access to a different module syntax that takes advantage of the keywords import and export. Let's convert that first export block.
```javascript
export const greet = (name) => 'Hello, ' + name + '!';
// OR
export default greet;
```
Then to access that code we could use
```javascript
import { greet } from './formalities';
// OR
import greet from './formalities';
```
What’s nice is that we can use both export and export default together. There's much more you can do with ES6 modules and I would definitely encourage you to check it out. require still has its place but I rarely use them now

* [Learn more about import](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
* [Learn more about export](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
