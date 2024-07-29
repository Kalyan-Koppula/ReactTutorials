## Components 
fxns with input and output.
some special way 

when is a fxn a react comp
- only one input 
- only one op that it returns
- u dont call this fxn as literall syntax , fxn()
- <Comp/>
- name should start with capital ( react will understand that span is native html and Span is user defined comp)
```js
const Comp = () => {
	return <div>hi</div>
}

const Comp = () => {
	return (<div>
	hi
	</div>)
}

const Comp = () => {
	return (
	<div>hi</div>
	<span>aa</span>)
	//not valid
}

sln is wrap in <></> or a div or sapan or other element


```

- <comp/> will always fail , even if ther is no comp natie html elem.
```js
componets can call other comps

const Comp = () => {
	return <input value='' />
}

const Othercomp = () => {
	return <Comp  />
}

```

how do i pass input parameter to a component., how to make the value of inpt dynamic -> who ever calls Comp should pass the value.

sln , pass 'lly  as passing html attrubutes to native elms

```js
<Comp value='12' attr2='v2' />

 Comp fxn definition will only recieve these values are  single bndled param {value:'12', attr2:'v2'}
```

> is there a limit ot the number of attribute that a html elemnt has ?

-> component will only get have one input which is an obj ,
key: vale pairs , key is attribute name , value is its value

ur inpt param {attri1:v1,attri2:v2,attr3:v3}

```js
lets says 
some called 
<Comp value='12' attr2='v2' />

const Comp = (props) => { //props = {value:'12', attr2:'v2'}
	so u can get value as 
	const v = props.value; and so on...
	return <div>hi</div>
}

this will also work 
const Comp = (attributes) => { // attributes ={value:'12', attr2:'v2'}
same wwill work here also 
const v = attributes.value
	return <div>hi</div>
}

props is suggested namen , its upto u to decide what to call this single object inpt 
```
Should i aslwasys use arrow function ? -> no need
```js
function Comp(props){
return <div>HI</div>
}
valid
```

react file can be named as .js or .jsx

- componet alwasys returns a jsx element.
## JSX
jsx is extended javascript
js + html -> jsx

u can write html inside js file

-> is all html valid jsx ? no 
jsx is strict 

- every elemetn should have closing tag / self closing 
`<br>` is valid html , but in jsx `<br/>`
- attribte names that u give to tags shold be in camel case.

`<input onclick=fx >` valid html but in jsx `<input onClick=fx />`
- in html u will gove class, here it is className. ()
- the prop names of ur componet should not be reserved js keywords.
- `<Comp if='value' let='asd />`
template literal syntax
```js
const Comp = () => {
	//inde js
	return (
	<div>hi/*insidehtml what if u eant ot run some js here {js expression}*/</div>
	)
}

example 

const Comp = () => {
	const v = 2;
	return <div>hi{v}</div>
}

inside js -> go to html -> use a tag , or fragmet
inside html -> go to js -> {}

const Comp = () => {
	const flag = true;
	let firstv=1,secondv=2;
	return (
		<>
			{
				flag ? 
				<>
					{firstv}
					<div>asda</div>
				</> : 
				<span>
					{secondv}
				</span>
			}
		</>	
	)
}
```

Prop destruturing
```js
<Comp value=12 />
const Comp = (props) => {
	let value = props.value
	return <div>{value}</div>
}

const Comp = (props) => {
	let {value} = props
	return <div>{value}</div>
}

const Comp = ({value}) => {
// some_internal_varibale = {value:12}; let value = some_internal_varibale.value
	return <div>{value}</div>// value is availble to u 
} 

const Comp = ({value: v}) => {
// some_internal_varibale = {value:12}; let v = some_internal_varibale.value // this whle line js does internally
	return <div>{v}</div> // v is avaulbel to you 
}

<Comp value=12 attr=1 attr1=2 attr2=3/>

const Comp = ({value, ...otherprops}) => {
	// otherprops = {attr:1,attr1:2,attr2:3}
	return <div>{value}</div>
}

```