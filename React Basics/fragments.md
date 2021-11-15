- let you group a list of child components without adding extra nodes to the dom.

We have a file 'FragmentDemo.js'. Let's have a look at it:
```jsx
class FragmentDemo extends Component {
    render() {
        return <h1>This is a react fragment.</h1>;
        <p>Hello there this is Shreya</p>;
    }
}
export default FragmentDemo;

> output: code unreachable
// the second line of <p> tag will not print.
```
- to help this issue out, we have to wrap the return elements inside a `div` tag. So lets do that:
```jsx
class FragmentDemo extends Component {
    render() {
        return (
            <div>
                <h1>This is a react fragment.</h1>
                <p>Hello there this is Shreya</p>
            </div>
        );
    }
}
```
- this will solve the issue. However will create an unecessary `div` outside which is sometimes not requried.
- so to *prevent creating any extra nodes (which are ofcourse of no use), we use something called fragments in react.*
- **Fragments wrap all the return content inside without creating any uncecessary** div which is very helpful.

```jsx
class FragmentDemo extends Component {
    render() {
        return (
            <React.Fragment>
                <h1>This is a react fragment.</h1>
                <p>Hello there this is Shreya</p>
            </React.Fragment>
        );
    }
}
```

if you want to make it more simpler..
```jsx
    render() {
        return (
            <>
                <h1>This is a react fragment.</h1>
                <p>Hello there this is Shreya</p>
            </>
        );
    }
```
`warning:` you cannot use key attribute for this shorthand so better use <React.Fragment> when using keys :)