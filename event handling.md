We've two cases of event handling:
- event handling in functional components
- event handling in class components	

# In functional components
```jsx
import React from "react";
function FunctionClick() {
     function clickHandler() {
        console.log("ching chang");
     }
 return (
   <div>
      <button onClick={clickHandler}>Click</button>
   </div>
 );
 }
export default FunctionClick;
```

- our handler (*clickHandler*) should be a function, and not a function call (`clickHandler()`) otherwise it will start functioning as soon as we reload the page (before clicking the button itself) and that is what we don't want.


- use onClick = {clickHandler} , not `onClick="clickHandler"`
---

# In class components
```jsx
import React, { Component } from "react";
class ClassClick extends Component {
	 clickHandler() {
		 console.log("Click");
		 }
		 render() {
			return (
				 <div>
					<button onClick={this.clickHandler}>Click class</button>
				 </div>
			);
		 }
}
export default ClassClick;
```

- we call the function with `this` keyword such that: **{this.clickHandler}**
- 