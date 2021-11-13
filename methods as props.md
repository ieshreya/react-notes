props: whenever a child component want to communicate, or access a value from a parent component, props are used.

### How to pass methods as props in react components
>1. in the parent component (**ParentComponent.js**), define the method
2. in the child component tag (**\<ChildComponent />**) , pass the method as a prop
3. in the child component (**ChildComponent.js**), access the method using the prop object
4. if you want to pass a parameter, use the arrow functions in tags (**\<button> tag in this case**)

ParentComponent.js
```jsx
import React, { Component } from "react";
import ChildComponent from "./ChildComponent";  
class ParentComponent extends Component {
	 constructor(props) {
	 super(props);
		 this.state = {
			 parentName: "Parent",
		 };
	 this.greetParent = this.greetParent.bind(this);
	 }
	 greetParent() {
	 alert(`Hello ${this.state.parentName}`);
	 }
 render() {
	 return (
		 <div>
		 	<ChildComponent greetHandler={this.greetParent} />
		 </div>
	 );
	}
}
export default ParentComponent;

```


ChildComponent.js
```jsx

function ChildComponent(props) {
 return (
 	<div>
		 <button onClick={props.greetHandler}>Greet Parent</button>	
	 </div>
 		);
	}
export default ChildComponent;

```

> as you can see in our child component, we used props as a parameter to access the `greetHandler` function from the parent component.


## Passing a parameter from a child component to a parent component
// how to pass parameters from the child component to the parent component -> we use arrow method in the return statement

ChildComponent.js
```jsx
function ChildComponent(props) {

 return (
	 <div>
		<button onClick={() => props.greetHandler("gimu")}>Greet 	  
		Parent</button>
	 </div>
   );
   }
```

ParentComponent.js
```jsx
 greetParent(childName) {
 alert(`Hello ${this.state.parentName} from ${childName}`);
 }
```

*Output: Hello Parent from gimu.*

