### Controlled components?
![[Pasted image 20211020005118.png]]

- form elements whose value is controlled by react is called controlled component

- how to deal with values that can change within the component? 
	- using state, setState

 - in the `onChange` method, we use setState to update the method

---
A simple form component inside our jsx component file `Form.js`
```jsx
 return (
	 <form>
		<label>Username</label>
		<input type="text" />
	 </form>
 );
 ```
 
-> right now, it is a static, uncontrolled component. To make it a controlled component, two steps are followed:
1. create a component *state* that will control the value of input element:

```jsx
export class Form extends Component {
 // step 1 
 constructor(props) { super(props);
	 this.state = {
	 username: "",
	 };
 }
 render() {
 return ( 
	 <form>
		 <label>Username</label><input type="text" value= {this.state.username} /> 
	</form>
   );
  }
}
export default Form;
```

2. Handling the *onChange* event:
```jsx
//below the constructor:

handleUsernameChange = (event) => {
	 this.setState({	
		 username: event.target.value,
	 });
 };
 
 //inside the form element, below the label tag:
  <input type="text" value={this.state.username} onChange={this.handleUsernameChange} />
  ```
  
  ### Working with form elements using controlled components:
  Steps are - 
  1. add the element HTML:

```jsx
 <div>
	<label>Comments</label> 
	<textarea> </textarea>
</div>
```
  2. assign the component state to element value:

```js
//change 1:
this.state = {
	 username: "",
	 comments: "",
 };
 
 //change 2:
 <textarea value = {this.state.comments}></textarea>
```
  3. assign an onChange handler to update the state:
```jsx
//change 1:
 handleCommentsChange = (e) => {
 	this.setState({
	 	comments: e.target.value,
     });
 };
 
 //change 2:
  <textarea value = {this.state.comments} onChange={this.handleCommentsChange}></textarea>
```
---
## Submitting the form
- add a submit btn with type="submit"
- assign a handler on `onSubmit` event on your form tag
```jsx
<form onSubmit={this.handleSubmit}>
```
- now we can define our handler:
```jsx
 handleSubmit = (e) => {
	console.log(`${this.state.username} - ${this.state.comments} - ${this.state.topic}`
  );
};
```
- add e.preventDefault() at the end of handleSubmit component to prevent it from reload after we submit the data
```jsx
handleSubmit = (e) => { 
	console.log( `${this.state.username} - ${this.state.comments} - ${this.state.topic}`
	);
e.preventDefault();
};
```
---

### Destructuring our component
now that we're done, let's destructure the component as its a good practice:

Normal File, inside the render method:
```jsx
 render() {
	 return (
	 <form onSubmit={this.handleSubmit}>
		 <label>Username</label>
		 <input
			 type="text"
			 value={this.state.username}
			 onChange={this.handleUsernameChange}
		 />
		 <div>
		 <label>Comments</label>
		 <textarea
			 value={this.state.comments}
			 onChange={this.handleCommentsChange}
		 ></textarea>
		 </div>
		 <div>
		 <label>Topic</label>
		 <select
			 value={this.state.topic}
			 onChange={this.handleTopicChange}
		 >
		 <option value="react">React</option>
		 <option value="vue">Vue</option>
		 <option value="angular">Angular</option>
		 </select>
		 </div>
		 <button type="submit">Submit</button>
	 </form>
	 );
 }
```
 
 
 Destructured file:
 
 ```jsx
  render() {
 const {username, comments, topic} = this.state;
	 return (
		 <form onSubmit={this.handleSubmit}>
		 <label>Username</label>
		 <input
			 type="text"
			value={username}
			 onChange={this.handleUsernameChange}
		 />
		 <div>
		 <label>Comments</label>
		 <textarea
			 value={comments}
			 onChange={this.handleCommentsChange}
		 ></textarea>
		 </div>
		 <div>
		 <label>Topic</label>
		 <select
			 value={topic}
			 onChange={this.handleTopicChange}
		 >
		 <option value="react">React</option>
		 <option value="vue">Vue</option>
		 <option value="angular">Angular</option>
		 </select>
		 </div>
		 <button type="submit">Submit</button>
		 </form>
	 );
 }
```