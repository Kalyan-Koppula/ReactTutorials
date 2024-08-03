31-07-2024

if u have an variable which has array, then u csn just render it as  {variable} inside return 

map will return new array, forEach dont
ForEach  => no one will store return value of forEach
return value of map => array of return value of each of iteration excution return value

ForEach will return undefined..
why u have to use forEach or map always  = (important)

child cannot pass data to to parent.
unidirectional flow only..

prop drilling - see example

in filter  return statement of callback fun inside it will alwasy be true or false. u cannot use jsx.

filter will include only the elementd in aray for ehich callback inside it returned true..

pure componnt => name is in your scope but a is not in your scope, so dont use it.. 


## adding interactivity
event listener => when click happens it will have callback, and it wil get event object-> when it is clicked, position etc...

event if it is click -> mdn will have method - check mdn

writing handler function call and defining it  - (Read from kalyans doc)


updation of html tags with the updated value will be done by Virtua;Dmo.. browser will paint it on actual DOM.. 


Hooks - 
methods that react api exposes..
react hooks  -> fishing hook ->
allow u to hook into component behaviour and change it

usestate -> rerender
effect -? rendering with sometime -< want to run fn at some time of your >i want to turn on motor after coming home > display this after 2 renders
memo->  calcluate value of var= fn(cal value) => assume that this func has to do something with chatgpt const img=chatgpt(generateimage())
callback-> function changes only when value changes not always



callback - aviods creating function -> fn1- 100, 2nd render fn1-200

usememo - u want to run and get output -> run this function only when state changes..

for smaller function dont use usememo.. coz seraching in cache and if not call fn and take from cache will take more time..

999 times diff value and 1 time new value then its waste..


render -< componet  u call returning html and displaying it is render



DAY - 3
1-10 number change -> u need to change elementabYiId.innerHtml u need to do 10 times..
Here we intoruce state 

Trigger > render > commit -> refer mapping..



DAY - 4 - 3-8-2024 master class
setState will always return undefined
and u can write callback fun inside setter fn of usestate

see setstate function calling.. by refernce
once state update react will go to that node and update but from thatn node till end of alll child it will re render - (swelt is shining is here)

remindeer : batching
choosing state structure - grping and ungrping - when to choose number, objecct
updating arr and obj in state
passing state to children
lifting state up
handle state update programatically - reducer 
usestate, useref


complete execetion of handle click >> update the state >> commit from VDOM to DOM


first execute synchrounous code
setstate do it later


a = {k:1}
a.k=2
 both are equal
a = {...,k:2}




re render happens	when u execute sestate - all these are state batching

batching was not there in react < 18>


batching
mututation and without mutation
state value -  array
updating with object, normal value, array


computed state = > keeping 2 currency - usd and inr
swiggy

useState and useContext triggers re render

useContext - dark theme - it should get reflected everywhere
in usecontext - if u read contect also it will re render

state update
parent or grand parent got re rendered
context got updated -> u dont have latest one so re render

On definition and execution all the hooks will be at the end EXCEPT usestate
and useref


histing - works for var and fn()

var a= 10 will be considered at top of file
and function fx()

const fx() - it will brrak

usememo will give u actual returned value
callback jjust refernec





