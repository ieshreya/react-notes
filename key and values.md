continued from [[list rendering]] :

- every key should be unique
- not accessible in the child components.
- console warns: *Each child in a list should have a unique "key" prop.*
- each item in our list should have a unique key. We can assign the key value by:
```jsx
 const personList = persons.map((person) => (
	 <Person key={person.id} person={person} />
 ));
```

- now our console will also not display that warning ;)

### Why we need keys?
- helps react in identifying the items from the list that are changed, added or removed.
- plays an imp role in handling the UI updates efficiently

## Using `index` as key
```jsx
const nameList = names.map((name, index) => <h2 key={index}> {name} </h2>)
```
- using index as a key can cause some serious UI issues.
- We should only use index as key if it satisfies some conditions:
	1. items should not have a unique id.
	2. list should be static, i.e it should not change
	3. list should never be reordered/ filtered