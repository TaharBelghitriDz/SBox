# sbox

the easiest and simple solution for react scalable state management

## Installation

```bash
npm install sbox-react
```

### first create store

all what you need is on the createState function

```javascript
import createState from "sbox-react";

const state = { s: "hi", r: { j: "j", m: "m" } };

// all what you need is return a partial from the state to update it
const store = createState(state, (currentState) => ({

  open: () => ({ s: "s - " + Date.now() }),
  close: async (e) => {
    const fetch = await ...
    //some workd here
    //

    // it's gonna merge the state and the object you return so you don't have to worry about anything

    return { s: { j : fetch} };
  },
}));
```

#### and use it on your components

```javascript
function Value = () => {
    // state is you current state with latest update
  const value = store.useStore((state) => state.s);
  return <h1>{value} around here ...</h1>;
}
```

### how to use methods

```javascript
function Value = () => {
  const value = store.useStore((state) => state.s);


  return <h1 onClick={()=> store.open()} >
            click me to update it ... {value}
        </h1>;
}
```

### sUpdate

easy function to update state, get an object as parameter and merge it with the state

```javascript
function Value = () => {
    // state is you current state with latest update
  const value = store.useStore((state) => state.s);

  return <h1 onClick={()=>
                        store.sUpdate({s :"changed by sUpdate function"})
                    }>
            click me to update it ... {value}
        </h1>;
}
```

### Why sbox over all ?

- Simple and un-opinionated
- Makes hooks the primary means of consuming state
- Doesn't wrap your app in context providers
- Can inform components transiently (without causing render)
- i made it :)
