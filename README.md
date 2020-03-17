# Intro to React State

## Learning Objectives
 - Learn about state
 - Learn how to declare state in a React component
 - Learn how to iterate over some data and render it

<!--SEI1 5:23 -->

## State

State is the data for a particular view of a React component.

Let's imagine we have a component that has a shopping cart.

At first, our cart is empty, so our `state` would likely have an empty array.

Then we add an item into our cart. We'd push an object like this one into our cart:

```js
{
itemName: 'Jar of Speculoos',
description: 'Imagine butter cookies dissolved in butter, made into cookie butter and stored in a jar. Stop imagining and now buy this!',
price: 6.99
}
```

Now our view of our shopping cart will change, based on the data or the `state` of the shopping cart.

### Objective
Let's build a tiny online store and render the items available to us.


## Render a list

![try console.table instead of console.log](https://i.imgur.com/wo7ayxR.png)

We want to be able to see an unordered list of our product names in the browser.

This is exactly what React is designed to do: render views based on data.

Let's set up our React app first.

**app.js**

```js
function App() {
    return (
      <div>
        <h1> Big Time Shopping </h1>
      </div>
    )
}

ReactDOM.render(
  <App />,
  document.querySelector('.container')
)
```

<!--SEI1 5:41 -->

Currently, our app has no `state` (no data for our view). That's ok! Not all components have to have `state`. A simple navigation bar that is just 'hard coded' can be a react component - some components are just for presentation.

However, in the case of our online store, we'll want a list based on our data, so we will add `state`.

`state` is a special key word in react. In order to use it, we used to have to set up a `constructor` function, like we did in Unit 1.

```js
import React, {useSate} from 'react'

function App() {
  const [produucts, setProducts] = useState([]) 
    return (
      <div>
        <h1> Big Time Shopping </h1>
      </div>
    )
}
```

We can look at our React dev tools and now see that our products are being stored in the `App` component's `state`.

![app state](https://i.imgur.com/XAxOGgh.png)

Inside the `return` of `render()` function is special. The syntax that is recognized is JSX. JSX is a mishmash of HTML and JavaScript. There are a few gotchas inside the return, for instance we can't console log. We'll see others during this unit.

Much like we did in unit 2, we can embed our data in the html. Let's put the first product in there for rendering. We have to wrap any JS we want to render in curlies `{}`.

```js
  return (
    <div>
      <h1> Big Time Shopping </h1>
      {products[0].name}
    </div>
  )
```
We should see the allen wrench show up.

We can use is the `.map` function. `.map` will iterate over every item, manipulate it in some way, and return the new array.

In our case, we want to make an unordered list:


```js
  return (
    <div>
      <h1> Big Time Shopping </h1>
      <ul>
        {
          products.map(product => {
            return <li>{product.name}</li>
          })
        }
      </ul>
    </div>
  )
```

<!--SEI1 5:54 after questions -->

With ES6, if our function is one line of code (and no more), we can skip the curly braces after the arrow and we can skip the return statement - it will implicitly return the one line.

```js
  return (
    <div>
      <h1> Big Time Shopping </h1>
      <ul>
        {
          products.map(product =>
            <li>{product.name}</li>
          )
        }
      </ul>
    </div>
  )
```

In our case, we may also want to show the price, so let's update our code:

```js
<li>{product.name} - {product.price}</li>
```

<!--SEI1 6:07  after questions -->
