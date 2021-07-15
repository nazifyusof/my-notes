# useReducer #

Can be used as replacement for useState if we need "more powerful state management"

Can be used when want to update a state that depends on other state. It may work in some cases but it could fail because of how React schedule state update. 

```
const [state, dispatchFN] = useReducer(reducer, initialState, initFn)
```

_state - The state snapshot used in the component rerender_

_dispatchFn - A function that can be used to dispatch a new action (ex. trigger an update of the state)_

_reducerFn (prevState, action) => newState - A function that is triggered automatically once an action is dispatched - it receives the latest state snapshot and should return the new update state_

_initialState - the initialState_

_initFn - A function to set the initial state programmatically_

## Ex. ##

```
const emailReducer = (state, action) => {
  if (action.type === 'USER_INPUT') {
    return { value: action.val, isValid: action.val.includes('@') };
  }
  if (action.type === 'INPUT_BLUR') {
    return { value: state.value, isValid: state.value.includes('@') };
  }
  return { value: '', isValid: false };
};

const [emailState, dispatchEmail] = useReducer(emailReducer, {
    value: '',
    isValid: null,
  });
  
//can call dispatch
const validateEmailHandler = () => {
dispatchEmail({type: 'INPUT_BLUR'});
}; 
//then can set a state based on other state
setFormIsValid(
  emailState.isValid
);

```



 