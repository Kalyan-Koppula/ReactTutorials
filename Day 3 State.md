## Why and What 
as discussed ystrday , we need some mechanism to keep track of some values over time , and u want ur component to be reactive( as in change the ui of the component he user does something on demand ) , 
2 problems 
- store value 
- Reactive componetn 
- Preserve value between two or more reactive cycles.

Sln:

useState

usage 

```js
write only on top level inside the component
dont call inside other hooks 
dont call inside loops or conditional

const Comp = () => {
	[a,b].forEach(e => {
		[s, ss] = useState(0)
	}) // not acceptable.

	const [state, setState] = useState(initialvalue);
	type of initialValue is any object , number ,booleab, symbol....,
}
```

[[Day3.canvas]]

```js
setState(newvalue)
setState((prevstate)=>{do something with prevstate and then return new state})

setState(precount=> return precount+1)
```

- UseState rule , always treate the state as immutable.
i.e., dont change it on ur own , alwasy use setState funtion to update the state.

why , 
2 things , 
1. y want to store a value between renders .
2. once u update a state u want ur view to be update i.e., trigger a render.

1. point will be statidife by the first argument that the usestate hook returns.
2. 2..............., who is doing the rerender , how react knows to do it ..

## types of value that u can store

some precautions u need to take .

state should be considered immutable ,
there is actually nothing stopping u from changing state by urself . but y not to do ? prathis wil answer.

> Aside: 
> in js lets talk about obj and array ...
>
	```
```js 
let a = 0;
a++ // allowed
const b =0 ;
b++ //not allowed

const ob = {a:1}; // ob point ing to 100 address at 100 u have variable a point to 200 address which has value 1.
ob.a =2 //allowed 

ob = {a:2} // not allowed


const ar = [1,2];
ar.push(3) //allowed
ar = [3,4,5] //not allowed 

```

```js
const Comp = () => {
	const [state, setState] = useState(0);
	u cant do state++;
const [state, sss] = useState({a:1});
state.a = 2; no one is stopping even if it is const 
but dont do it , no rerender will happen.
}
```