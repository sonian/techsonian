---
layout: post_page
title: Three Reflux Tricks
---

By [John Bintz](https://twitter.com/johnbintz)

We’ve been using Reflux, a Flux architecture library, in one of our
apps, and it’s made reasoning out the flow of data and interactions
within the user interface easier. Reflux is simple to extend, allowing
you to easily abstract out common interactions and reduce boilerplate
code. Here’s three of the tricks we’re using to make using Reflux even
nicer.

## Making Store Updates & Retrieval Simpler

We use Immutable for the data in each store. However, using Immutable
data structures in the React view layer can start looking real ugly,
with data.get(‘something’) strewn all about the code. Since we use
CJSX to define the DOM, we definitely prefer brevity in our HTML code,
so why not use the simpler JavaScript representations of our store’s
data? If you’re using Reflux.connect to plug a store directly into a
component, the getInitialState method on each store decides what data
should be placed into the component. If we have each store house its
data in its state property, we can give the same getInitialState
method to each store, one that transforms that state property into a
JavaScript object:

```javascript
Reflux.StoreMethods.getInitialState = -> @state.toJS()

MyStore = Reflux.createStore
init: -> @state = Immutable.fromJS(one: "two")

MyComponent = React.createClass
mixins: [Reflux.connect(MyStore, 'myStore')]
render: ->
<h1> {@state.myStore.one}</h1>
```

How about making those store updates easier? Normally, you call the
store’s trigger method to notify listeners (other stores or view layer
components) that the store’s data has been updated. trigger takes the
data you want to send to the other components as a parameter, which,
for us, is always the contents of the store. So let’s make it
super-easy to both update the store’s immutable data and notify the
listeners with that data:

```javascript
Reflux.StoreMethods.updateState = (state) ->
@state = state
@trigger(@getInitialState())

MyActions = Reflux.createActions(['change'])

MyStore = Reflux.createStore
listenables: [MyActions]
init: -> @state = Immutable.fromJS(one: "two")
onChange: -> @updateState(@state.set('one', 'three'))
```

## Fast Action Wiring

Sometimes I’m feeling lazy and I don’t want to have to keep using
MyActions.change in my view components — I just want to call change,
like how stores can use onChange. We’ve come up with a simple solution
to make me a lazier programmer: `Reflux.wireUp`:

```javascript
Reflux.wireUp = (actions) ->
obj = {}
creator = (value) ->
(args...) ->
(e) ->
e.stopPropagation()
e.preventDefault()

value(args...)

for action, handler of actions
obj[action] = creator(handler)

obj

MyComponent = React.createClass
mixins: [Reflux.wireUp(MyActions)]
render: ->
<a onClick={@change()}>Change!</a>
```

Every base level action is now available as a method on the store
itself. Call that method to create an event handler. Any parameters
provided to the method are passed along to the action listener, so
that you can do things like:

```javascript
@state.items.map (item) =>
<a onClick={@change(item.id)}>{item.name}</a>
```

## Browserify Your Action Listeners

If you’re using Browserify to manage your JavaScript frontend code,
you can use the require-globify plugin and a bit of Reflux code to put
all your action listeners into individual files and load them with one
line, greatly reducing the size and complexity of your actions files:

```javascript
Reflux.populateListens = (actions, listens) ->
_.each(listens, (code, req) ->
[parts..., final] = req.split('.')

reducer = (base, part) -> base[part]
base = parts.reduce(reducer, actions)

base[final].listen (args...) -> code.call(this, args..., actions)
)

MyActions = Reflux.createActions(['create'])

//# there's a file in this directory called create.coffee whose
//# module.exports defines the listener function for MyActions.create.
Reflux.populateListens MyActions, require('./MyActions/*', hash: true)
```

Using these Reflux tricks, we’ve made it easier to manage our data,
wire up our actions, and define those actions in a standard
way. Hopefully they can help you manage your Reflux-driven web
application better, too!
