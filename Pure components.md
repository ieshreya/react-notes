### Pure component?
> pure components prevents unecessary re-rendering of webpage/app and hence acts as a performance boost.

> pure component means our component will work only if there is a change in prevState otherwise it will not rerender -- performance boost

> its good to ensure that all the child components are also pure component (why? - ) to avoid unexpected behaviour (what kind of? -) our component will not update/rerender even if there's a change in state ;) 

> never mutate the state. always return a new object that reflects the new state

there's another way of creating class components in react. This way is by extending the pure component class from react. let's have a look at it:

```jsx
import React, { PureComponent } from "react";
class PureComp extends PureComponent {
 	render() {
 return <div>This is a pure component.</div>;
 }
}
```

### Difference b/w component and pure component
- Regular Component
	- do not implements the `shouldComponentUpdate` method. Always returns true by default
- Pure Component
	- implements `shouldComponentUpdate` with shallow props and state comparison.
![[Pasted image 20211026001738.png]]

#### Shallow Comparison (SC)
- Primitive Types
	- a (SC) b returns `true` if a and b have the same value and type
	- eg: string 'Shreya' (SC) string 'Shreya' returns `true`
- Complex Types
	- a (SC) b returns `true` if a and b reference the exact same object.
	- eg:
	```js
	let a = [1, 2, 3];
	let b = [1, 2, 3];
	let c = a;
	let ab_eq = (a === b);    // false (bcoz both the obj. do not reference to the same obj.)
	let ac_eq = (a === c);    // true
	```
	![[Pasted image 20211029225952.png]]