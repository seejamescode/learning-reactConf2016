# Wilds of Data Handling
(Check out code-cartoons.com for detailed flows.)

## Flux
To fix the cycle of predictability.

Flux = Action > Dispatcher > Store > View (and repeat)

Facebook had a serious bug where it would tell you that there is a new message, but disappear when you actually clicked on it. This was caused by spaghetti data flow.

Flux said to do a unidirectional data flow (as seen above). But what do each of these pieces do?

- Action Creator - provides an API of all possible state changes. It formats the actions so that there is an easy list of all possible actions. This is great for a new dev on the team to go to and understand what is possible.
- Dispatcher - Action is dispatched to every registered callback. It is the messenger to all of the store.
- Store - The over-controlling bureaucrat because it does not allow anything not going thru the official channels of the Action Creator and Dispatcher.
- View and Controller View - The view is a presenter of updated store.

## Redux
To split the state from the logic and handles changes immutably.

What is Hot Loading?
Hot Loading is being able to see your change in code without losing your state store.

What is time-travel debugging?
Being able to see the history of actions taken by the user/data that ran into your app's bug.

For Redux, we need a new role:

- Reducer - A reducer makes your data immutable. This is by making a copy of store before the action is committed and placing that history in a nice array.

## Relay (on GraphQL)
Connects the graph you have on the cloud and the graph you have on your own app's server.

Redux handles a lot of problems for you because it is already caching the data with immutable data handling.

GraphQL makes it easy to grab the little amount of data you actually need. This is declarative in the actual component itself.

Relay links up Redux and GraphQL smoothly. It bundles up the queries from all of the components to GraphQL from a local cache, then gives it back to the Redux process.

