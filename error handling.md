- called when there's an error during rendering in a lifecycle method (above mentioned) / or in the constructor of any child component.

### Error Handling Methods:

```
- static getDerivedStateFromError
- componentDidCatch
```

### Steps:
1. **static getDerivedStateFromError**
2. **componentDidCatch(error, info)**

-> are called when there's an error during render(), in a lifecycle method or in constructor of child component.