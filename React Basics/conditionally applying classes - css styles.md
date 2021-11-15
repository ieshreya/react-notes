- we can primary apply a class based on state/ prop of the component.

StyleSheet.js
```jsx
function Stylesheet(props) {
	let className = props.primary ? "primary" : "";
	return (
	 <div>
		<h1 className={className}>CSS</h1>
	 </div>
	 );
}
```

App.js
```jsx
function App() {
 return (
	 <div className="App">
		<Stylesheet primary={false} />
	 </div>
 );
}
```

style.css
```css
.primary {
	 color: violet;
}
.font-xl {
	font-size: 72px
}
```

> in case we have to apply multiple classes, template literals is the best option to go with. Let's have a look at it:

```jsx
 <h1 className={`${className} font-xl`}>CSS</h1>
 ```
 
 ## Using CSS modules
 - are named by `fileName.module.css`
 - are used for specific components
 - helps preventing the accidential use of a stylesheet that is defined for another component
 - classes are locally scoped by default
 
 #### Importing CSS modules file
 
 - importing normal css files
```jsx
//App.js --------
// importing..
import './appStyles.css'

// component
class App extends Component {
render()
	return(
		<div className="App">
			<h1 className='error'> Error </h1>
		</div>
	)
}

//Style.css --------
.error {
 	color: red;
}
```
 - importing `modules.css` files

```jsx
//App.js --------
// importing..
import styles from './appStyles.module.css'

// component
class App extends Component {
	render()
		return (
		<div className="App">
			<h1 className={styles.error}> Error </h1>
		</div>
	)
}

//Style.css --------
.error {
 	color: red;
}
```