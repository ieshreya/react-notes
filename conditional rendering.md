- used to show/hide some HTML elements based on some conditions. Here's when conditional rendering is needed.
- Conditional rendering in React = conditions in JS
- we have 4 different approaches:
	1. if/else
	2. element variables
	3. ternary conditional operator - `recommended`
	4. short circuit operator - `recommended`


### 1. if/ else 
- here in the example below, we have a state called `isLoggedIn` and two welcome statements, *Welcome Shreya* and *Welcome Guest*.

at first, we have - 
```jsx
//UserGreeting.js
import React, { Component } from "react";

class UserGreeting extends Component {
 constructor(props) {
	 super(props);
	 	this.state = {
			 isLoggedIn: false,
		 };
 }

 render() {
	return (
		<div>
			 <h1>Welcome Shreya</h1>
			 <h1>Welcome Guest </h1>
		</div>
	 );
 }
}
export default UserGreeting;
```


Goal: Display *Welcome Shreya *when isLoggedIn is true and *Welcome Guest* when it's false. 
We can achieve this using if/else. Let's see how, inside the render component  - 

```jsx

 render() {
	 if (this.state.isLoggedIn) {
 		return <h2>Welcome Shreya</h2>;
 	} else {
 		return <h2>Welcome Guest</h2>;
  	}
 }
```

### 2. element variables

```jsx
 render() {
	 let message;
	 if (this.state.isLoggedIn) {
	 	message = <h2>Welcome Shreya</h2>;
	 } else {
		 message = <h2>Hello Guest</h2>;
	 }
	 return <h2>{message}</h2>;
 }
```

here `message` is the variable which stores the element to be rendered

### 3.  ternary conditional operator
> Pros: it can be used within the JSX elements (whereas it couldn't in the above mentioned 2 examples)
> Easiest one of all!

```jsx
 render() {
	 return (
		 this.state.isLoggedIn ?
		 <h2>Welcome Shreya</h2> :
		 <h2>Hello Guest</h2>
	 )
}
```


### 4. short circuit operator 
- just a specific case of ternary operator approach.
- when we want to render nothing, or something then we use this approach
- Let's say in this example, we want to display *Welcome Shreya* when `isLoggedIn` is true and nothing when `isLoggedIn` is false. Then we use short circuit operator
 ```jsx
  render() {
	 return this.state.isLoggedIn && <h2>Welcome Shreya</h2>;
	 }
 ```