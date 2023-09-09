---
layout: ../../layouts/MainLayout.astro
title: Props Revisited
description: Hello and welcome to this blog I am writing this blog as a revision for react So today we are going to re-visit a topic in react call props
---

#### Date: Dec 14, 2022

Hello and welcome to this blog I am writing this blog as a revision for react So today we are going to re-visit a topic in react call props

So the first question is why do we need props ?

- props make our data , component reusable
- props are immutable
- data passed from outside of component

## How to pass props at a very basic level

```js
<CustomComponent name="radhe-krishna" />
```

- so here we are passing `prop -> name` in custom component
- where name is the `key` and `radhe-krishna` is value
- Internally every _`jsx`_ element transpiles to object(POJO)
- therefore , props are nothing but objects with key value pair

## How to access props in a component ?

### Consuming props in a Component

```js
function CustomComponent(props) {
	return <div>{props.name}</div>;
}
```

- prop is an object , so to access the values of props
  we can use dot operator
- But why props.name ?
- remember we wrote our `key` as `name`
- so basically we are using that key to access the value(prop) we defined in custom component
- As we already know component transpile to object ? right! so props is pre-defined key-name inside JSX object
- whenever we pass any props to custom component , we can access the prop using props.propName

> do you know before react we having been using props in native html elements like anchor(href),img(src)

### can we use custom props in native _`DOM`_ elements ?

- Repeat After me, NO! we can't pass custom props to native dom elements

```js
Basic Introduction Completed!
```

### Advance Props Guide

Before learning more about props , we can have one small basic props exercise, so here you go

```ruby
- open code sandbox (react environment)
- make a custom component call `Info.jsx`
- render the custom component in app
- pass basic details `firstname, lastname, age, city, profession` as a prop
- consume that information in `Info` component and display
```

#### I myself is doing this mini-exercise while writing this article 😃🥳

[My solution for exercise](https://4rctog.csb.app/)

If you did it ? Well Done! you know props
If got stuck with non-string props or destructuring no worries we will cover this together, continue reading 😊

#### A Friendly Water Reminder if you haven't

![Water Reminder](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/eyq7qwdvx3x0if7k5ag0.jpg)

## What did you learn new with that exercise ?

- Passing `non-string props, multiple props, consuming multiple props`
- Let me dissect it step by step
- From the previous exercise, I passed props to custom component in this way :

```js
<Info
	firstName="Dheeraj"
	lastName="Purohit"
	age="23"
	city="Mumbai"
	profession="Developer"
/>
```

- Well Everything was in double quotes ""
- Also called as String Props
- We could do it differently for non-string props like `age or any boolean props`

### Non-String and Multiple Props

#### A) Non-String

```js
<Info
	firstName="Dheeraj"
	lastName="Purohit"
	age={23}
	isIndian={true}
	city="Mumbai"
	profession="Developer"
/>
```

- Did you noticed we added {} braces around non-string props values
- hey but still it looks weird right ? we are passing multiple props affecting the readability.

#### B) Multiple Props

```js
export default function App() {
	const propsData = {
		firstName: "Dheeraj",
		lastName: "Purohit",
	};

	return (
		<div className="App">
			<Info {...propsData} />
		</div>
	);
}
```

- For Multiple props we can store our props value in object
- `propsData` is an object having our props value
- We are passing multiple props to `Info` component using `object` spread operator, so simple and readable right!

[javaScript info for spread syntax](https://javascript.info/rest-parameters-spread)

```scala
PAY ATTENTION!
```

### 3) Consuming multiple Props and Object as a Prop

#### A) Consuming Multiple Props

```js
export function Info(props) {
	const {
		firstName,
		lastName,
		age,
		city,
		profession,
		isIndian,
	} = props;

	return (
		<div>
			<ul>
				<li>{firstName}</li>
				<li>{lastName}</li>
				<li>{age}</li>
				<li>{city}</li>
				<li>{profession}</li>
				<li>{isIndian ? "Indian" : "Non-Indian"}</li>
			</ul>
		</div>
	);
}
```

- we can consume multiple props using object destructuring
- ` const { firstName, lastName, age, city, profession, isIndian } = props`
- after destructuring we can directly use the name of props in UI part of (after return element)

#### B) Using Multiple Props (Object) without destructuring

- there are multiple patterns followed in react , so destructuring is one of them
- we can also access prop value by using `props.keyName.propsName`
- Lets see how to do that

```js
export default function App() {
	const propsData = {
		firstName: "Dheeraj",
		lastName: "Purohit",
	};

	return (
		<div className="App">
			<Info propsData={propsData} />
		</div>
	);
}
```

- we are passing props our old _`key`_ value pair
- propsData is key for props
- now lets consume it

```js
export function Info(props) {
	return (
		<div>
			<ul>
				<li>{props.propsData.firstName}</li>
				<li>{props.propsData.lastName}</li>
			</ul>
		</div>
	);
}
```

- remember i mentioned we are going to use `props.keyName.propsName`
- so here we are directly using props
- re-iterating `props` is general key for accessing props `propsData` is our `keyName` and `propsName` are `firstName and lastName`

> Refactoring time

- we have learned something new , so to make it concrete try to refactor the previous exercise and see how readable our code becomes.

```java
Ending Note!
- i might have missed some parts of props, but tried to put it here as a part of my revision
- if you find this article helpful, like, share with others who is learning react
- if you find any spelling mistake, wrong term used do let me know in comments and your feedback about this blog

Happy Coding
Jai Shri Krishna🙏💜
```
