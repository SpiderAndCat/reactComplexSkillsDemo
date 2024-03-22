# reactComplexSkillsDemo
This repo showcases, through an interactive ToDo web app, my understanding of more complex React skills:
- **Complex State** (nested JS objects and arrays),
- **Destructuring** (Arrays, Objects, and nested Arrays and Objects),
- **Controlled Components** (reflecting state across components),
- **Event Handling** (across components)

 ***Access the live demo*** here: (WIP)

## Code feature overview

### Complex State
```js
//show code here
```

### Destructuring
```js
//show code here
```

### Controlled Components
```js
// the <input> "value" will be tied to a state, 'inputText'
const [inputText, setInputText] = useState("");
...
// The <input> field will only show the value of 'inputText'. The field will properly update to show the string being typed, thanks to the inclusion of "value={inputText} />"
<input onChange={handleChange} type="text" value={inputText} />
...

```

### Event Handling (across Components)
```js
//show code here
```
