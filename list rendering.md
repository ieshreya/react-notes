## Way 1
```jsx
 const names = ["Shreya", "Samridh", "Nanu"];
 const nameList = names.map((name) => <h2>{name}</h2>);
 return (
	 <div>
		{nameList} 
	 	{names.map((name) => <h2>{name}</h2>)} 
	 </div>
 );
```

## Way 2
In case we've more than one parameters, we create objects for our list elements:

```jsx
 const persons = [
 {
	 id: 1,
	 name: "Shreya",
	 age: 19,
	 skill: "Web Development",
 },
 {
	 id: 2,
	 name: "Samridh",
	 age: 14,
	 skill: "Game Development",
 },
 {
	 id: 3,
	 name: "Mom",
	 age: 36,
	 skill: "pretty much everything",
 },
 ];
 
 // now we can map our items like:
 const personList = persons.map((person) => (
<h2> I am {person.name}. I am {person.age} years old and I know working with {person.skill} </h2>
 ));
 return (
	<div>
	 {personList}
	</div>
);
```



> but the recommended way (which is also followed in real life projects) is to refactor the JSX into a separate component. And that is our **WAY 3** . Let's have a look at it:

## Way 3
- the object data will be same as in above *way 2*.
NameList.js (our main file):
```jsx
 const personList = persons.map((person) => (
 	<Person person={person} />
 ));
```

Person.js (separate file for our JSX component):
```jsx
import React from "react";
function Person(person) {
	 return (
		 <div>
			<h2> I am {person.name}. I am {person.age} years old and I know working with {person.skill} </h2>
		 </div>
	 );
}
export default Person;
```

- So this is how we refactored our code and made our code cleaner. We should always follow this approach.

read next in continuation: [[key and values]]