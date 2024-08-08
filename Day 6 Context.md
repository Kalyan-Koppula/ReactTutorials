Creating a context.
```js
file name MyContext.js

import {createContext} from 'react';

const MyContext = createContext(initialValue);  // out {Provider: ractcomponent}

export default MyContext;

```

Read the context value 

inside any componet.

```js
import {useContext} from 'ract'
import MyContext from './MyContext'
const Comp = () => {
	const ContextValue = useContext(MyContext);
}
```

rading from context and do something and modify this value to pass updated val to all ur children.

```js
import {useContext} from 'ract'
import MyContext from './MyContex
const Par = () => {
	const ContextValue = useContext(MyContext);
	const updatedcontextvalue = somecal(contextvalue)
	retunr (
		<>
		<Child1 />
		<Child2 />
		</>
	)
	will be changed to 
return (
		<MyContext.Provider value={updatedcontextvalue}>
			<Child1 />
			<Child2 />
		</MyContext.Provider>
)

here u need not pass updated context value to the chidl as proprs ,
once the child reads context using useContext(MyContext) it will automaticaally get the updated value.
}
```

prathi to write about signature of createContext and useContext..


```js
const Comp = () => {

let colorvar
return (
<Child color={colorvar} />
)
}
```
