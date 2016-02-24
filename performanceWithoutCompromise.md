# Performance without Compromise
Netflix has to develop for streaming devices way slower than your typical laptop.

## Unidirectional Data Flow

The problems with observation instead:

- Lateral channel between components
- Race condition factory
- Flux makes it better
- Boilerplate vs read-only Relay style

When Netflix started solving this problem, Redux did not exist. They ended up having a top-down approach. A state change in a component was bounced up to each parent component and then affected each parent's children.

A huge struggle was with handling mixins like the video component itself. How do use all of your existing components, but swap out different things to try like redux and relay?

With higher-order components, it is much more clear about where data and state feed into.

## Always Be Declarative

Focusing with refs was dangerous for Netflix because they could break that component just by changing another component that wraps it. So the solution was to focus on IDs of say a movie for each movie tile. That way, you could add

Golden Rule: No refs, ever.

## Being Fast

Lag is noticed from user input after 100ms. Animations needed to be at least 60fps.

The most basic screen for Netflix app has 150 elements.

So how did they do when they measured their performance?

Lag was at 200ms with higher-order components:
1.2ms per render, 6 higher-order components per list, 8 lists

But they loved what higher-order components did for them. So adding, tranducers was able to to take off 50ms and bring them down to 150ms.

## Separate Props

Separate props between static and dynamic. That way, you don't waste time with your reducers adjusting the static props that will never change:

```javascript
const staticStyle = {x: 10};
const dynamicStyle = {img: url(...)};
```
