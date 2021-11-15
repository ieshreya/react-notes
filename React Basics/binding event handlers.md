we'll discuss 4 approaches to bind event handlers in this doc:
- using bind() method - performance issues, not recommended
 - using arrow functions - performance issues, still good for smaller functions
- binding in the constructor - recommended in react docs 
- using arrow func as a class property - recommended in react docs

there are many ways to bind event handlers, but what is the need to do so?
Let's have a look at an example below:
```jsx
class EventBind extends Component {
	 constructor(props) {
	 super(props);
	 this.state = {
	 	message: "Hello",
 };
 }

 handleClick() {
	 this.setState({
	 message: "Goodbye",
	 });
 	console.log(this);
 }

 render() {
	 return (
		 <div>
			 <div>{this.state.message}</div>
			 <button onClick={this.handleClick.bind(this)}>
			 Click bind
			 </button>
		 </div>
 );
}
}
export default EventBind;
```

> the result on clicking the btn will be `undefined` *for console.log(this) inside the handleClick function* as this keyword has nothing to do with the message property of constructor (out of scope). **'this' keyword is undefined because this used with a function returns 'window' object on the browser and 'global' object inside nodejs environment. Since 'react strict mode' is enabled, it is returning 'undefined'.**
>  So to solve this problem, we use binding.


## using bind():
```jsx
 <button onClick={this.handleClick.bind(this)}> Click </button>
```
this code will work fine now and our click btn will work as we coded it.

## using arrow functions:
```jsx
 <button onClick={
 	() => this.handleClick()
	}>Click</button>
```

another approach is by calling it inside an arrow function. remember, we HAVE to *call* it! (handleClick() using paranthesis) :)

> Now both these approaches are good enough for small applications, but on large scale, they may casuse performance issues. 

## binding in the constructor - best one 🟣
this 3rd approach is seen in most of the codes, even in the official react docs.
here we bind the event handlers in the constructor, not in render method (as seen in previous approaches).

```jsx
constructor(props) {
 super(props);
	 this.state = {
		 message: "Hello",
	 };

 this.handleClick = this.handleClick.bind(this);  
	//this above line
 }
 ```
 
 and now we can simply call our handleClick function in our button element such that:
 ```jsx
  <button onClick= {this.handleClick} >Click</button>
 ```
 
 
 ## using arrow func as a class property
 this 4th approach is to simply define the handleClick function as an arrow function:
 ```jsx
  handleClick = () => {
 	this.setState({
 		message: 'Goodbye'
 	})
 }
 ```
 
similarly (as above), we can now simply call our handleClick function in our button element such that:
 ```jsx
  <button onClick= {this.handleClick} >Click</button>
 ```
 