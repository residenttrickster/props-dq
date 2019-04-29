# Discussion Question: Declarative Programming

In this repository is an `index.html` file with some pre-written HTML. Open this file in your browser and discuss the following:

1. Looking at the page in the browser, discuss which parts of the page look repeatable.
2. Looking now at the HTML, discuss which bits of the HTML are repeatable.
3. If you were to abstract out the repeatable portions of the given HTML, which bits would remain static and which would need to be dynamic?

ex:
```HTML
<h1>Hello!</h1>
<h1>Goodbye!</h1>
<h1>Whoa!</h1>

<!-- h1 tag is static, exclamation point is static, the greeting is dynamic, so the abstracted version might look like... -->

<h1><!-- INSERT GREETING HERE -->!</h1>
```

4. Create an array to store data in a way that mirrors the dynamic portions of the data

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
```



There is another file in this repository called `index-react.html` with some pre-written HTML and JSX that, in the browser, looks identical. Discuss the following:

5. What is different about the pure HTML written in `index.html` and the mix of HTML and JSX written in `index-react.html`? What is the same?

**Bonus:**

6. Try writing your own component using JSX to create the abstracted HTML you created in step 3.

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

7. Using the array you created in step 4, try to operate on that array to create programmatically create your JSX

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

8. If you got through step 7, try adding additional data to your data structure. What happens in the browser? What is the correlation between the data and the DOM? Given this correlation, what would be an easy way to add, remove, or update information on the DOM?
