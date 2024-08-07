
What is the problem with the state now , 

for normal states(number , boolean and stuff) its easy to handle,
for complex state like array and object , its hard , and u might have to repeate the same syntax of spreading and updating multiple times all through ur component .

and udates like this are prone to errors , what if in a chain of state updates u have messed a single on in between then all ur further state updates are useless.


```js
cnost Comp = () => {
	const [state, ss] = useState({s:0,hc:0});
	const calc = ()=>{returned a negative value by mistake}
	ss({...state,hc:calc});
	ur state will become {s:10,hc:-1} // for exampe 

	here hc :-1 is perfectly alrigt but according to the game logic this is impossible.

}
```

To avoid this , wouldn't it be nice if we had a programattic wasy of updating things , so as to avoid impossoible state values.

solution is reducer,

what is reducer 

reducers is a piece of funtion that is in charge of doing the upates , 

how,

how to write a reducer function,
[[Day5.canvas]]

piece of code which takes an 
```js
action is generaly {type: what u want to do , payload: additional data }
function reducer(state, action){
	conat {type} = action
	switich (type) {
		case Eat:
			callcyalte or dome swith ur state 
			return updated state without mutation
		case HIt:
		case Sleep:
	}
}
```

```js
const Comp = () => {
	function reducer(state, action){
	conat {type} = action
	switich (type) {
		case Eat:
			callcyalte or dome swith ur state 
			return updated state without mutation
		case HIt:
		case Sleep:
	}
}
	const [s, ss] = useState(inital);

	const [stae,dispatch] = useReducer(reducer,initial)
dispatch(ip<any>) ->
		  react internally calls the redicer function 
		  with reducer(state, ip<any> 'this u passed to dispatch as ip')
		  the state will track the ouptu of reducer fn.

}
```


signature of useReducer fnx : ip1: fx, ip2: optional any, opt: [state, fx]

## useRef




