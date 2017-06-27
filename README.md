# Liquid-route
```
  npm i -D liquid-route
```
This is a collection of route element and animation objects based on [`element.animate`](https://developer.mozilla.org/en-US/docs/Web/API/Element/animate). Which will make it super easy for you to do animated routing.

This mainly consist of the following animation objects

1. FaderAnimation: Next route will fade in and current will fade out.
2. PopAnimation: Next route will pop from center and current route will implode.
3. SlideLeftAnimation: Next route will slide from right while current one slides to left.
4. PushNSlideAnimation: Routes will scale down and slide.
5. AppearFromBottomAnimation: Next route will fade and appear from bottom and sit on top of current route.
6. AppearFromRightAnimation: Next route will fade and appear from right and sit on top of current route.

## Sample
<img src="https://im.ezgif.com/tmp/ezgif-1-43b21b18f3.gif" />

## Route element
`liquid-route` is the route component which you would need to use in order animate between routes. It takes a prop named animator which is a animation object

```jsx
  import Router from 'preact-router';
  import LiquidRoute, {FadeAnimation, PopAnimation} from 'liquid-route';
  import 'liquid-route/style.css';
  .
  .
  .
  return (
    <Router>
      <LiquidRoute animator={FadeAnimation} path="/" component={(url, cb)=>{
        return System.import('./Components/Home/Home.jsx').then(module => module.default);
      }}/>
      <LiquidRoute animator={PopAnimation} path="/profile" component={(url, cb)=>{
        return System.import('./Components/Profile/Profile.jsx').then(module => module.default);
      }}/>
      <LiquidRoute animator={PopAnimation} path="/profile/:pid" component={(url, cb)=>{
        return System.import('./Components/Profile/Profile.jsx').then(module => module.default);
      }}/>
    </Router>
  );
```

## Animator object
`Animator` object is a javascript object which exposes two methods
1. `getEntryAnimation` - returns animation object used to play entry animation of a route
2. `getExitAnimation` - returns animation object used to playexitentry animation of a route

Both of the above ☝ methods return an object having the following properties
a. animation: array of animation object used to play the entry/exit effect
b. options: an object of options taken by [`element.animate`](https://developer.mozilla.org/en-US/docs/Web/API/Element/animate) api.

## Inspiration
While some basic animator objects come with the bundle, [here](https://tympanus.net/Development/PageTransitions/) is where the most of the transition inspiriation is drawn from.

## You creative?
Send PR if you wanna add new animators in the repo, happy to include 😊.

### Note
In order for the transitions to work, please declare all routes as `liquid-route`.


**P.S.** Tried and tested most of the animations are easily doable with this route element.
