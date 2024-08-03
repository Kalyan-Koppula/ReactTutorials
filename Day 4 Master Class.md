- state -> u can store vaue between renders ( explain later in detail and what difference does it make if i use regular variable).
- to trigger a rerender -> call the setState function.

## Variations of calling setState function.

- u can call it normally lik e `setState(newValue)`,
- u can do `setState(callbackfxn)`.

signature of the setState function ,

- it is a fucntion.
- input can be any js value (obj, array ,num, boolean , symbol) or function also.
- doesnt return anything  ,implicit  undefined returned by js.

what is the type and signatur eof the callbackfxn that i can give asinput to setState.

() => {} -> input is previous state value , u shuld return the value of the next state.

```js
(prevState) => {//some calculyato,
return prevstate+5
},

in genreal we simplywrite it as 

prevState => prevState+5
```

## Aside
```js
const logger = (fx, ip1,ip2) => {
    console.log('fxn called');
    console.log( fx(ip1,ip2));
}

const add =(a,b) => {
    return a+b
}


logger(add,1,2);

//logger(add(),1,2)-> what is the problem prathi ?

const ff = (x,y) => add(x,y)
logger(ff,1,2)
```

```js
Crude implementation of setState
const setState = (v) => {
    if typeof v === 'function' {
        const uv = v(prevstate)
        // some mechanism to update ur state to uv
    }
    else {
        // some mechanism to update state to v
    }
}
```
```js
//const updateCallback = prevCnt => prevCnt+1
	//setCnt(updateCallback)
	const computation = (vl) => {
	//some calculation....
	return updatedvl
	} 
	//setCnt(computation)
	//setCnt((prevCnt)=>compation(prevCnt))
```
## What is rerender ?
```js
const Comp = () => {
const [cnt, setCnt] = useState(0);
const handleClick = () => {
	setCnt(prevCnt => prevCnt+1)
}

return (
<button onClick={handleClick} >count is {cnt}</button>
)

}
------------------------------------------------

const Comp = () => {
const [cnt, setCnt] = useState(0);
const handleClick = () => {
	setCnt(prevCnt => prevCnt+1)
}

return (
<>
<Child setCnt={setCnt} />
<button onClick={handleClick} >count is {cnt}</button>
</>
)

}

const Child = ({setCnt}) => {
const handleClick = () => {
	setCnt(prevCnt => prevCnt+2)
}

return (
<button onClick={handleClick} >I am child btn</button>
)

}


```

[[Day4.canvas]]


```js
Regular varibale vs state 

const App = () => {
  let regcount = 0;
  const [cnt, setCnt] = useState(0);
  const handleClick = () => {
    regcount++;
    setCnt((prevCnt) => prevCnt + 1);
    console.log(`state is${cnt} and reg is ${regcount}`);
  };
  return <button onClick={handleClick}>count is {cnt}</button>;
};
```

Prathi to add the content for batching....

## Choosing state structure

- sate can have any value number , boolean , string , object or array 

- u can have any number of state , 
	but it will slowly become complicated to maintain each and every state.
-  u can put all states in an object as a single component state -> problem is while updating u will not understand which part of the  state to be updated
state1,state2,state3 ........... state = {state1: v1,state2:v2, state3:v3}

`const [compState,setCompState] = useState({state1:v1,staet2:v2,state3:v3})`

both have problems 
find a border line , where state that are unrelated to each are better to be separated , and group all states that are related in an object. ( user's discretion is required).

```js
u r making a game 
which will track score , high score and number of lives ( after 3 lives gameover or something )

const Game = () => {
it makes sense that score and hihgscore can be related to each other 
const [gameScores, setGameScores] = {score:0,highScore: retrievefromDB};
lives state ....

}

```
Prathi will add content.........
## Treat state as immutable value while reading and updating as well

>Aside
>refer [[Day4.canvas|Day4]]

Prathi will read and add for array without mutation.


Q? u gropded score and hihgscore in prevoius example , how to update them , will it not be confusing?

one word ans  is update without mutation.

```js

const Game = () => {
it makes sense that score and hihgscore can be related to each other 
const [gameScores, setGameScores] = {score:0,highScore: retrievefromDB};

const updateScore = (newscore) => {
	setGameScores({...gameScores, score:newscore});
}

same prathi will handle highscore updation 

and one more example to be added for array.

}
```

```js
Mutstion example
export default function App() {

  const [scores, ss] = useState({ s: 0, hs: 0 });

  const hc = () => {
    const us = scores.s + 1,
      uhs = scores.hs + 2;
    ss((ps) => {
      return { ...ps, s: us };
    });

    scores.s = 10;

    //some logic that is dependant on the state for example
    console.log(scores.s);
    //expected to have value depending on the user clicks

    ss((ps) => {
      return { ...ps, hs: uhs };
    });
  };
  return (
    <>
      <button onClick={hc}>Click</button>
     {JSON.stringify(scores)}
    </>
  );
}
```

![[Pasted image 20240803190330.png]]

prathi to explain console output ?

## state structure and computed state.

Prathi to write about choosing  state structure -> think whatsapp or face book example.

```js
const SwiggyRiderEstimation = () => {
	const [oredrD,so] =  useState({restAdd: '', homeAdd: '', distance: 4});
	conat [rider,sR]= useState({name:'',speed: 30});

	return (
		<div>ETA {orderD.distance/rider.speed}</div>
	)
}

const SwiggyRiderEstimation = () => {
	const [oredrD,so] =  useState({restAdd: '', homeAdd: '', distance: 4});
	conat [rider,sR]= useState({name:'',speed: 30});
	const calTim = () => {
		return orderD.distance/rider.speed
		//assume this is expensive
	}
	return (
		<div>ETA {calTim()}</div> // prathi u remember me?
	)
}


---- jst know it ----
will discuss once i start useCallback vs useMemo // signatures of these two, along with usage
dont get scared please.
const SwiggyRiderEstimation = () => {
	const [oredrD,so] =  useState({restAdd: '', homeAdd: '', distance: 4});
	conat [rider,sR]= useState({name:'',speed: 30});
	const calculatedTime = useMemo(() => {
		return orderD.distance/rider.speed
		//assume this is expensive
	},[orderD.distance,rider.speed]);
	return (
		<div>ETA {calculatedTime}</div>
	)
}
```

>Aside 
> **Prathi : always check the signature of the functions u are writing and reading** 
```js
console.log([1,2].toString()) //1,2  same as Array.prototype.join(',')
console.log({a:1}.toString()) //[object Object]
const fx = () => {}
console.log(fx.toString())  
```

## Passing Data.

you remember , 
when we said that state udates triggers a rerender the compont is rendered and the sub tree aswell.?

u already kow that , if u want to pass daata to a component u did it using props 

till now u jhave passaded only static data in the props 

`reactive value` -> any vale that is kept track of , and is somehow responsible for rerender , be it at any level

```js
const Gp = () => {
const [gst, sgst] = useState();
// i want my gchild to update my state aslo.
retrn (
<P gst={gst} sgst={sgst}/>
)
}

const P = ({gst, sgst}) => {
//even if i dont care for gst , i still have to get and pass it.
const [cst,scst] = useState();
//even if this is not my state , sinc i have to read it , ia m declaring.
return (
<>
<C gst={gst} scst={scst} sgst={sgst} /> //mistake people make is scst={scst()}
<div>{cst}</div>
</>
)
}

const C = ({scst, ...props}) => {
//wanted a state , which his parent also should be able to access.
//i want to update state.
//how to scst()? get it in props
const handleClick =() =>{
scst(newValue);
const {sgst} = props; //overaction, prathi to explain
sgst(someValue);
}
return (
<div>HI prathii </div>
)
}
```


## Beginner mistake

```js
**Template**
//import ract decalrtion 
//import other compoents
//import utils and styles if needed

const Comp = (props) => {

	//decalrae states
	//decalre refs
	//declare local variables

	//any util functions with usecaslaksff..

	//effects -> write the effect that runs only first empty dep arrary , then write the rest.

	return (
	)
}

//export ur componet 
```

```js
**Hoisting**
fx()
gx()

const fx = () => {}
function gx(){}

//trns in to 
function gx(){}
fx() // fx is accessed before decalration.
gx()

const fx = () => {}


--------------
fx()
gx()

var fx = () => {}
function gx(){}

//turns to 
function gx(){}
var fx;
fx() // fx is undefined , cant call as funtion.
gx()

fx = () => {}
```

```js
**Mistake**

const Comp = (props) => {
	cosnt [s,ss] = useState(0);
	const handleClick = (event) => {
		ss(newValue);	
	}
return (
<button onClick=(handleClick()) />
)
}

and wondering y inifinte rerenders 
explain? 
prathi will answer.
```

```js

** MAny poeple dont relaize **
** this is a problem **
index.js
const P = () => {
	const C1 = () => {} // C1 will redecalred each time P rerender
	const C2 = () => {}
	return (
	<>
	<C1 />
	<C2 />
	)
}


-- instead make it like this --
const C1 = () => {}
const C2 = () => {}
const P = () => {
	return (
	<>
	<C1 /> 
	<C2 />
	)
}

```