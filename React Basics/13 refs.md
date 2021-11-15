### What are refs?
- helps accessing the DOM nodes directly within react.
- eg: focusing an input element in a login form automatically when the page loads.
- refs can be used with class components.
- to use them in functional components, use of Hooks is initiated.

![[Pasted image 20211116010707.png]]
- We will see two approaches below
---
## #1 Approach:
- using `createRef()`.
- create a class component with a constructor. It returns an input field.

Step 1 - create a ref within the constructor:
```jsx
this.inputRef = React.createRef()
```


Step 2 - attach the ref into render method:
```jsx
<input type="text" ref={this.inputRef}>
```
we now have the reference to input element.


Step 3 - calling the focus method on this input element.
```jsx
componentDidMount(){
     this.inputRef.current.focus()
 }
```

done🎉

**Final Component**:

```jsx
import React, { Component } from "react";

class RefsDemo extends Component {
    constructor(props) {
        super(props);
        this.inputRef = React.createRef();
    }
    componentDidMount() {
        this.inputRef.current.focus();
        //   console.log(this.inputRef);
    }
    clickHandler = () => {
        alert(this.inputRef.current.value);
    };
    render() {
        return (
            <div>
                <input type="text" ref={this.inputRef} />
                <button onClick={this.clickHandler}>Click</button>
            </div>
        );
    }
}
export default RefsDemo;
```

---
## #2 Approach
- using callback refs. *older approach to create refs.*

Step 1 - create a property with `null` assigned as its value inside constructor. This is our ref:
```jsx
this.callbackRef = null
```

Step 2 -  create a method that assign DOM element to this ref:
```jsx
this.setCbRef = e => {
    this.callbackRef = e
}
```

Step 3 - attach the ref to input element:
```jsx
<input type="text" ref={this.setCbRef}>
```

Step 4 - add the callback ref to `componentDidMount` method and apply the focus method:
```jsx
componentDidMount(){
	if(this.callbackRef){
		this.callbackRef.focus()
}}
```

*Note: react calls the callback ref with DOM element when the component mounts; and call it with null when it unmounts.*

**Final Component:**
```jsx
import React, { Component } from "react";

class RefsDemo extends Component {
    constructor(props) {
        super(props);
        this.callbackRef = null;
        this.setCbRef = (e) => {
            this.callbackRef = e;
        };
    }
    componentDidMount() {
        if (this.callbackRef) {
            this.callbackRef.focus();
        }
    }
    render() {
        return (
            <div>
                <input type="text" ref={this.setCbRef} />
            </div>
        );
    }
}
export default RefsDemo;
```