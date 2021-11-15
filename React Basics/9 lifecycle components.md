- lifecycle methods ONLY exist in the class components
- BUT Hooks (*useEffect*) can make this kind of method exist in Functional Components

### Lifecycle methods
  There are 4 phases of lifecycle methods:
1. [[9.1 mounting]]
	- called when an instance of a component is being created/ inserted into DOM
 1. [[9.2 updating]]
	 - called when a component re-renders due to changes in props/ state
 2. [[9.3 unmounting]]
	- called when a component is removed from DOM
 3. [[9.4 error handling]]
	 - called when there's an error during rendering in a lifecycle method (above mentioned) / or in the constructor of any child component