# Dynamic Context API #

pass not only data, but also function

_auth-context.js_

```
const AuthContext = React.CreateContext({
	isLoggedIn: false,
	ctx.onLogout: () => {} //just write as empty for IDE autocompletion
})

export default AuthContext
```

_whatever.js_

```
import AuthContext...

const ctx = useContext(AuthContext)

//{ctx.isLoggedIn)  data
//onClick={ctx.onLogout} function
```

_app.js_

```
import AuthContext...

const logoutHandler = () =>{
....
}


<AuthContext.Provider value={{
	isLoggedIn: isLoggedIn,
	onLogout: logoutHandler
}}>
		//all children here have access to AuthContext
</AuthContext.Provider>
```
