# SELECT #

There are two ways to change selected value for select component

## Option 1 ##

```
const func = (props) => (
{

    const items = props.options;
    const selectedItem = useState();
    return (
    <select value={selectedItem}>
        {
            items.map((item) => {
                return <option value={item.Name }>{item.Name}</option>;
            })
        }
    </select>);
}

```

## Option 2 ##

```
const func = (props) => (
{
	const items = props.options;
	const selectedItem = ** handle by onChangeHandler **
	
	return (
	<select value={selected}>
        {items.map((item) => {
			if (selectedItem == item.Name){
				return <option value={item.Name } selected>{item.Name}</option>;
            }
            else{
            	return <option value={item.Name }>{item.Name}</option>;
            }
        }
    </select>);
}
```
