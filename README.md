# Discussion Question: Declarative Programming and JSX


### Declarative Programming

In this repository is an `index.html` file with some pre-written HTML. Open this file in your browser and discuss the following:

1. Looking at the page in the browser, discuss which parts of the page look repeatable. Now looking at the HTML, discuss which bits of the HTML are repeatable.
2. If you were to abstract out the repeatable sections, which bits would remain static and which would need to be dynamic? In other words, which parts of the HTML are always the same (static) and which parts are unique to each section (dynamic)?

ex:
```HTML
<h1>Hello!</h1>
<h1>Goodbye!</h1>
<h1>Whoa!</h1>

<!-- h1 tag is static, exclamation point is static, the greeting is dynamic, so the abstracted version might look like... -->

<h1><!-- INSERT GREETING HERE -->!</h1>
```

3. Eventually real data will be used in this application. Considering that you have many repeating sections of your page and that each section has various **properties** which need to be filled in, how might your data be structured?

ex: 
```HTML
<!-- If your abstracted component looks like this:  -->
<h1><!-- INSERT GREETING HERE -->!</h1>

<!-- and your desired HTML looks like: -->
<h1>Hello!</h1>
<h1>Goodbye!</h1>
<h1>Whoa!</h1>
```
```js
// then you might need an array that looks like this:
let greetings = [
  {phrase: "Hello"},
  {phrase: "Goodbye"},
  {phrase: "Whoa"}
]
// at a minumum, each h1 needs to know what phrase to print as a greeting
```

### JSX
There is another file in this repository called `index-react.html` with some pre-written HTML and JSX that, in the browser, looks identical. Discuss the following:

4. What is different about the pure HTML written in `index.html` and the mix of HTML and JSX written in `index-react.html`? What is the same?

5. Try writing your own component using JSX to create the abstracted HTML you created in step 2.

ex: 
```jsx
function Greeting(props){
  return <h1>{props.phrase}!</h1>
}

ReactDOM.render(
  <div>
    <Greeting phrase="Hello"/>
    <Greeting phrase="Goodbye"/>
    <Greeting phrase="Whoa"/>
  </div>,
  document.getElementById('root')
)
```

6. Using the array you created in step 3, try to operate on that array to programmatically create your JSX

ex: 
```jsx
let greetings = [
  {phrase: "Hello"},
  {phrase: "Goodbye"},
  {phrase: "Whoa"}
]

function Greeting(props){
  return <h1>{props.phrase}!</h1>
}

ReactDOM.render(
  <div>
    {greetings.map(greeting => <Greeting phrase={greeting.phrase}/>)}
  </div>,
  document.getElementById('root')
)
```

note: JSX can render not only individual JSX elements, but *arrays* of JSX elements as well. Consider the above call to `greetings.map`: `map` will return an array containing `Greeting` components. These components will render in that order.

7. If you got through step 6, try adding additional rows of data to your array. What happens in the browser? What is the correlation between the data and the DOM? Given this correlation, what would be an easy way to add, remove, or update information on the DOM?
