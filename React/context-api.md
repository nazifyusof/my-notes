# Context API #

# Example #

component-wide, "behind-the-scenes" state storage. No need to have a long prop chain :D

Need to listen to the context. There are two ways; auth context consumer or react hook.


1) React useContext Hook (recommended)

_auth-context.js_

```
const AuthContext = React.CreateContext({
	isLoggedIn: false
})

export default AuthContext
```

_whatever.js_

```
import AuthContext...

const ctx = useContext(AuthContext)
```

_app.js_

```
import AuthContext...

<AuthContext.Provider value={{
	isLoggedIn: isLoggedIn
}}>
		//all children here have access to AuthContext
</AuthContext.Provider>
```



2) auth context consumer

_auth-context.js_

```
const AuthContext = React.CreateContext({
	isLoggedIn: false
})

export default AuthContext
```


_app.js_

```
import AuthContext...

<AuthContext.Provider value={{
	isLoggedIn: isLoggedIn
}}>
		//all children here have access to AuthContext
</AuthContext.Provider>
```

```
<AuthContext.Consumer>
		//takes a child which actually be a function. the argument will be the context data
</AuthContext.Consumer>
```

## limitations ##

1) it can be great for app/component- wide state, but not replacement for component configuration

2) react context is not optimized for high frequency changes. use Redux!!!

3) React context also shouldnt be used to replace all component communications and props. components should still be configurable via props and short "prop chains" might not need any replacement
















