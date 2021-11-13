- called when an instance of a component is being created/ inserted into DOM.

### Mounting methods:
```
- constructor
- static getDerivedStateFromProps
- render
- componentDidMount
```

## Steps:
1. **constructor(props)**
- get called whenever a new component is created.
- constructor used for? 
	- initializing state
	- binding event handlers
- `warning:` never make HTTP requests within a constructor
- always call super(props) in constructor

2. **static getDerivedStateFromProps**
- sets the state

3. **render**
- only required method
- read props, state and return JSX
- `warn:` don't change state // interact with dom // or make ajax calls

4. **componentDidMount**
- called only once
- invoked immediately after a component and all its children components have been rendered to DOM
- `perfect place to cause side effects: ` i.e we can interact with the DOM // make ajax calls to load data

---
```jsx
class LifecycleA extends Component {
    constructor(props) {
        super(props);

        this.state = {
            name: "Shreya",
        };
        console.log("Lifecycle A constructor");
    }
    static getDerivedStateFromProps(props, state) {
        console.log("Lifecycle A getDerivedStateFromProps");
        return null;
    }
    componentDidMount() {
        console.log("Lifecycle A componentDidMount");
    }
    render() {
        console.log("Lifecycle A render");
        return <div>Hello Shreya</div>;
    }
}
export default LifecycleA;

> Output:
//Lifecycle A constructor
//Lifecycle A getDerivedStateFromProps
//Lifecycle A render
//Lifecycle A componentDidMount
```
