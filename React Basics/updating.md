 - called when a component re-renders due to changes in props/ state.

### Updating methods:
```
- static getDerivedStateFromProps
- shouldComponentUpdate
- render
- getSnapshotBeforeUpdate
- componentDidUpdate
```

### Steps:
**1. static getDerivedStateFromProps(props, state)**
- called everytime a component re-rendered
- sets the state
- `warn: ` don't make HTTP requests

**2. shouldComponentUpdate(nextProps, nextState)**
- dictates if component re-render or not
- performance optimization
- `warn: ` don't make HTTP requests // call setState()

**3. render()**
- only required method
- read props/ state and returns JSX
- `warn: ` don't make ajax calls // change state or interact with DOM

**4. getSnapshotBeforeUpdate(prevProps, prevState**
- called right before changes into the virtual DOM
- capture info about DOM
- method returns: null/ any value. this returned value be put as a third parameter to next method.

**5. componentDidUpdate(prevProps, prevState, snapshot)**
- called after finishigh of re-render videos
- cause side effects!

---
LifecycleA.js : 
```jsx
// LifecycleA.js
import React, { Component } from "react";
import LifecycleB from "./LifecycleB";
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
    shouldComponentUpdate() {
        console.log("Lifecycle A shouldComponentUpdate");
        return true;
    }
    getSnapshotBeforeUpdate(prevProps, prevState) {
        console.log("Lifecycle A getSnapshotBeforeUpdate");
        return null;
    }

    changeState = () => {
        this.setState({
            name: "Samridh",
        });
    };
    componentDidUpdate(prevProps, prevState) {
        console.log("Lifecycle A componentDidUpdate");
    }
    render() {
        console.log("Lifecycle A render");
        return (
            <div>
                <div>Lifecycle A</div>
                <button onClick={this.changeState}>Change state</button>
                <LifecycleB />
            </div>
        );
    }
}

export default LifecycleA;
```

LifecycleB.js : 

```jsx
// LifecycleB.js
import React, { Component } from "react";

class LifecycleB extends Component {
    constructor(props) {
        super(props);

        this.state = {
            name: "Shreya",
        };
        console.log("Lifecycle B constructor");
    }
    static getDerivedStateFromProps(props, state) {
        console.log("Lifecycle B getDerivedStateFromProps");
        return null;
    }
    componentDidMount() {
        console.log("Lifecycle B componentDidMount");
    }
    shouldComponentUpdate() {
        console.log("Lifecycle B shouldComponentUpdate");
        return true;
    }
    getSnapshotBeforeUpdate(prevProps, prevState) {
        console.log("Lifecycle B getSnapshotBeforeUpdate");
        return null;
    }

    componentDidUpdate(prevProps, prevState) {
        console.log("Lifecycle B componentDidUpdate");
    }
    render() {
        console.log("Lifecycle B render");
        return <div>Lifecycle B</div>;
    }
}

export default LifecycleB;
```

> outputs seen:
![[Pasted image 20211024014847.png]]
```
// on running the app.js:
Lifecycle A constructor
Lifecycle A getDerivedStateFromProps
Lifecycle A render
Lifecycle B constructor
Lifecycle B getDerivedStateFromProps
Lifecycle B render
Lifecycle B componentDidMount
Lifecycle A componentDidMount


// after clicking 'changing state' btn:
Lifecycle A getDerivedStateFromProps
Lifecycle A shouldComponentUpdate
Lifecycle A render
Lifecycle B getDerivedStateFromProps
Lifecycle B shouldComponentUpdate
Lifecycle B render
Lifecycle B getSnapshotBeforeUpdate
Lifecycle A getSnapshotBeforeUpdate
Lifecycle B componentDidUpdate
Lifecycle A componentDidUpdate