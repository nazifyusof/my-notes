# useEffect #

_UseEffect optimization_ 

Instead of checking for every state change when inputing data into textbox, we can check 500ms after the we finish typing. 

```
useEffect(()=>{
	const identifier = setTimeout(()=>{
		console.log('checking form validity');		
		setFormIsValid(
			enteredEmail.includes('@') && ...
		);
	}, 500);

}, [enteredEmail])
```

To run in every component/parent rerender you need to use:

```
 useEffect(() => {
    // don't know where it can be used :/
  })
```

To run anything only one time after component mount(will be rendered once) you need to use:

```
 useEffect(() => {

    // do anything only one time if you pass empty array []
    // keep in mind, that component will be rendered one time
    // (with default values) before we get here
  }, [] )
```

To run anything one time on component mount and on data/data2 change:

```
const [data, setData] = useState(false)
const [data2, setData2] = useState('default value for first render')
useEffect(() => {
  // if you pass some variable, than component will rerender after component 
     mount one time and second time if this(in my case data or data2) is changed
  // if your data is object and you want to trigger this when property of 
     object changed, clone object like this let clone = JSON.parse
     (JSON.stringify(data)), change it clone.prop = 2 and setData(clone).
  // if you do like this 'data.prop=2' without cloning useEffect will not 
     be triggered, because link to data object in momory doesn't changed,
     even if object changed (as i understand this)
  }, [data, data2] )
```
