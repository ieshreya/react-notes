   - called when a component is removed from DOM.

### Unmounting Methods:

```
- componentWillUnmount
```

### Steps:
1. **componentWillUnmount**

- invoked immediately *before* a component is unmounted.
- `warn: ` never call setState method
- eg. of use
	- cancelling network requests, removing event handlers, cancelling subscriptions, invalidating timers.