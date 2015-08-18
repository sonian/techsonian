---
layout: post
title: "From Backbone To React: Our Experience Scaling a Web Application"
category: "Sonian Technology"
author: Murilo Pereira
---

At Sonian we have a small team building interactive visualizations where companies can better understand their massive amounts of email data. Building this kind of program is non-trivial: data needs to be synchronized between servers and complex interfaces through user interactions or otherwise while at the same time having the user perceive it as “feeling right”. Like other software disciplines it’s a combination of engineering and art.

As engineers we want to write our programs so that they have as few bugs as possible and are easily extendable, and as a company delivering value to customers we want stable features delivered quickly. Reconciling these objectives is a universal problem which is made easier in software engineering through the use of patterns and tools.

MVC

One pattern used to help with building contemporary web applications is MVC, conceived in the 1970s as a pattern for separating concerns in software programs, still popular today. Backbone is a well-known implementation of MVC where you build programs with object-oriented constructs: models and collections encapsulate data and views respond to user interactions and mutate the browser DOM. Objects communicate with each other through method calls and asynchronous events. We started this project using Backbone simply because that’s what we were more comfortable with, having using it extensively (and arguably successfully) since 2011.

Scaling Backbone

The complexity of the software systems we are asked to develop is increasing, yet there are basic limits on our ability to cope with this complexity.

Grady Booch

As we progressed through requirements, we had built collapsible panes, modals, popups with dynamic and navigatable content, full-text search filters, data sorting and pagination, and so on. Every one of these parts had to work in concert so that the UI represented the right context for the sequence of actions a user applied in any of multiple available interconnected interactive D3.js visualizations.

The code behind the features turned complex fast and we reached a point where a fair portion of effort was spent on maintenance. This situation is certainly familiar to most.

Graphs of stateful objects

Contemporary event-based MVC architectures can be viewed as a graph of stateful nodes communicating asynchronously.

In Backbone, particularly, despite following best practices and using complementary tools like Marionette, it’s likely that as the codebase evolves it ends up with:

Singular models dispatching events handled by multiple views
View A handling events from View B and vice-versa
Dispatched events causing chain/cycle reactions
An “event bus” where a dispatched event is handled by multiple objects
Typical Backbone Architecture

This kind of construction makes it hard to reason about the program. In addition to global mutable state there are events being dispatched likely causing multiple objects to change their state, which in their turn may dispatch even more events, possibly in ways you didn’t anticipate, making the program harder to extend and debug.

Programs that use state in a haphazard way are very difficult to understand. For example, if the state is visible throughout the whole program, then it can be assigned anywhere. The only way to reason is to consider the whole program at once.

Concepts, Techniques, and Models of Computer Programming

While it’s still entirely possible to build complex and useful programs using this kind of architecture (people have been doing it for years), maybe there’s a better way to write software where we don’t spend so much effort juggling with complexity unrelated to the actual problem at hand.


Enter React

An alternative tool for helping build large-scale web applications is React. Open-sourced by Facebook, React is a “library for creating user interfaces”, and it works by having the programmer express how their UI should look like at any point in time and having React automatically manage UI updates when the underlying data changes, obviating the need for explicit event observation or manual DOM mutation.

(…) programmers did not know how harmful complexity is, and secondly they did not know either, how much complexity can usually be avoided if you give your mind to it.

Edsger W. Dijkstra

The basic unit of construction is the component, which is essentially a function: composable by definition. Components are lightweight, in-memory representation of the DOM, and as their input changes React diffs these representations and batch applies the minimal set of changes required on the real DOM. The best part is that when using React you don’t have to think about any of this: just build components! React does the hard work under the hood.

This is in our opinion a much less leaky abstraction for synchronizing program state with its visual representation than any of the current solutions. It allows you to build programs using functions and data structures rather than framework-specific constructs or markup, and it makes entangling logic from your problem domain with observables a thing from the past.

The React Way

React draws a lot of inspiration from functional programming. It promotes immutability through the clear separation of props and state and encourages writing functions (components) that are free from side-effects and always return the same values (DOM representation) given the same inputs (props).

The functional model of computation combined with immutable data and one-way dataflow makes it much easier to reason about your program, greatly facilitating extension and debugging.

Our Approach

We got to know React late 2013 through the Clojure community, which quickly adopted it as a solution for theDOM problem. Our transition to it started by replacing a complicated composite, nested Backbone view that showed related word clouds side by side and allowed the user to perform interactions with either individual or groups of words. The existing implementation involved a lot of state and several events. It was hard to understand and had noticeable lag when the word clouds were too big. It had been a few weeks since we wanted to start using React, so we took this opportunity to see if it could better handle complexity. After literally one day of learning we started the transition, and after two days we had replaced the view with a React component with less code and more features. Its performance with even bigger word clouds was smooth even though we didn’t write a single line thinking about performance and it integrated nicely with every other part of the Backbone application.

We considered that the experiment validated the power of React, and since then we replaced almost all of the Backbone code: models and collections are now pure functions returning immutable data, namespaced by regular JavaScript objects and views are now React components. Note that we could have continued using Backbone models and collections, because React doesn’t care about what your data looks like. It doesn’t tell you how to talk to servers, or what routing construct to use, so you’re free to choose the tools and patterns you find best. In our case it looks like the following:

A single mutable reference to immutable application state (a database, conceptually)
“State manager” with state-changing transactions that are passed down to components as props
Virtually no use of state in components
Our React Architecture

If you know om this certainly looks familiar.

The application state is an immutable hash map provided by mori, which we use to represent every piece of data. Transactions are pure functions that return transformations of the current application state, which the state manager uses to transition to new states. With state and its possible transitions isolated to a single place, the rest of the application is essentially just logic for displaying data. This approach gives us a model of time for free, since the state manager has access to the application state history. With time, application-wide undo and redo is trivial.

Wins

Adding features needs much less changing of previous code to account for new behaviors. Components are naturally decoupled, meaning code diffs are mainly additions.
Codebase reductions. Not as dramatic as folks on Prismatic have seen, since we haven’t transitioned to ClojureScript yet.
Less time fighting MVC frameworks and libraries to make things work. React has only one major “concept” (the component), which makes it a very simple abstraction in contrast.
Performance improvements achieved through adding a single, generally short, idiomatic function. Conversely, performance improvements in MVC systems are achieved by minimizing DOM interactions through improvised caching and reduced usage of data-binding in key areas via ad-hoc, non-idiomatic code changes that generally require extensive comments in order to be explained and justified.
Future plans

Sonian already uses ClojureScript and om in other internal projects and we’ll be transitioning to that soon.

Conclusion

React is a powerful tool that we found to be objectively better than contemporary MVC frameworks. It provides a simpler abstraction with the collateral benefit of delivering faster performance. It’s helping us build UIs that would be nearly impossible to build using current alternatives under our current constraints.
