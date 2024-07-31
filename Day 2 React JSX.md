
[[Day2.canvas]]
## Inline styles 

```js
const Comp = () => {
return (
<div style = {{backgroundColor: 'red'}}>
)
}
```

`{{}}` is nothing but {} definintion inside {} template ...
## render conditions


```js
const Comp = () => {
return (
if conditon {
	<div style = {{backgroundColor: 'red'}}>
}
else {
	<span></spam>
}

)
}
or ternary 

conditon ? <div />: <span />

render contetn if condiotn met else nothing

{condition && <></>}


const Comp = () => {
return (
	!internet && <div style = {{backgroundColor: 'red'}}>oops no net </div>
)
}

```

## rendering lists


```js
const Comp = () => {
return (
	[<div/>,
	<div/>,
	<div/>]
)
}

const Comp = () => {
const v = [<div/>,
	<div/>,
	<div/>];
return (
	{v}
)
}

const Comp = () => {
cons names = [ prathi, kalyan]
const elms = names.map(n=><div>{n}</div>)
return (
	{elms}
)
}

const Comp = () => {
cons names = [ prathi, kalyan]
return (
	{names.map(n=><div>{n}</div>)}
)
}

```

- use only map or filter , only these two function return a array as ouptu.

## Passing data 

```js

const GrandChild = ({type}) => {
	return (
		<div> im a {type} coorditnat </div>	
	)
}
const Child = ({point, type})=>{
return (
<>
<div> x cord is {point.x}</div>
<div> y cor is {point.y} </div
<GrandChild type={type}/>
</>
)
}

const Parent = () => {
	return (
		<Child point={{x:1, y:2}} type={'cartesian'}/>	
	)
}
```

here type is drilled from parent to gchild , child is not using it but still u need to pass , 
because , parent can tgive data to gchil directly , why? parent is not having gchild in his render statement.

chaining is possible 

```js
[1,2,3].filter(e=>e<2).map(e=><div>{e}</div>)
```

## Pure Componet 

if u run ur compl with sme input 2 different times , its hould nt return 2 differnt outputs

```js
let a =1; // not acceptable 
const Comp = ({name}) => {
const r = random number generator // acceptable 
return <div>hi {name} {a} {r}</div>
}
<Comp name='prathi'/> // hi prathi 1 1.00
a = 2;

<Comp name='prathi'/> // hi prathi 2 1.23
```

## Adding interactivity 

in vj , evenets , elemts , u want to perform some callback on  given event 
click , hover , paste, cut , ............

elem.ddEventlIstern (type, callback )

callback -> implicityly get the event object as input.

omclick onpaste........, we hve to use camel case

```js
const Comp = () => {
const clickhandler = (event) => {//do wahtevr with event obj};
	return (
		<div onClick = {clickhandler()} /> //wrong
		<div onClick = {clickhandler} /> //correct
		<div onClick = {()=>{console.log('clicked');clickhandler()}} /> 
		
	)
}
```


## Challenge

### users click on ur componetn s ten times , then show a differnt screen
```js
let a = 0;
const Comp = () => {
	const clickh = () => {a++};
return <button onClick={clickh} />
}

a=100;
<Comp />

// woll not work anyone can chage a 

try another wasy 


const Comp = () => {
let a = 0;
	const clickh = () => {a++};
return <button onClick={clickh} >{a}</button>
}

<Comp /> -> what happens -> compo will generate html like 
<button onclick=clickh>0</button> -> gets added to ur dom , then no one take inchrge to update the dom again ..
```
Problem staremnt -> u wasnt some state of componetn , that u can update , and that update should be painted on the screen ( html shpould get this updates somehow)..

this is where state comes in 

useState , hook 

```js
const comp = () => {
 const time = somevalue that might change;
 const greeting = useMemo(()=>grretingoftheDAYAI(time),[time]) // expensive 
retunr (
<div>{1greeting}</div>
)
}
```

iinpu out 
1       a    check anser is in cacneh run fxn and store its value in cache 
2     b 
1     retireve from memory i lhave 1 already input its ou is a 


const image = chapgpt('generate prathis image')


