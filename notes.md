the virtual DOM (document object model)

- what is the different between the virtual DOM and the real DOM?
    - virtual DOM
        - can't directly update html
        - acts as a copy of the real DOM which can be manipulated and updated with a page refresh
        - more of a pattern than a specific technology
        - synced with the real DOM with 'react-dom'
    - real DOM
        - directly updates and manipulates html
        - creates a new dom / full repaint if it is updated
        - an object based representation of an html document and an interface for maninupating that object
    - the key is 'diffing'
        - the virtual DOM recognizes what needs to be updated and just updates that aspect, from - one state vs the next state

    - is the virtual DOM the same as the shadow DOM?
        - no. the virtual DOM is a pattern that is built into a variety of frameworks including react (and vue)
        - the shadow DOM is useful for styling, for things like making sliders and other built in CSS tools.
        - the shadow DOM is built into browsers and is not a pattern at all.

- react limitations
    - react is a library not a framework
        - pros and cons - a library is something that enhances your existing code. a big selling point was that you could just use it for small parts within other code.
    - because its a library, it lets you roam free - some people prefer a framework that directs where your files should go. gatsby or next.js are the most popular frameworks that show where your components should go but still uses react

    - react is fairly large
        - if you have guardrails in place its largeness shoudn't effect you too much.

    owned by facebook
        - it is regularly maintained. it is open  sourced, yes, but there is a specific team making all the decisions. limitations are privacy (bc facebook) and transparency.
    - the documentation is mostly up to date, but it doesn't have enoguh information on functional components vs class based, even though they're the future of react.
    the documentation isn't linear and hard to navigate. this means that the learning curve is really difficult.

- jsx
    - bread and butter of react
    - short for javascript xml. allows you to write javascript with an html-like template syntax. this is not the same thing as just putting html in your javascript.
    - not writign html or a string that gets inserted into html. 
    - the templates that you use produce elements that represent objects
    - you CAN write react without jsx - you could use React.createElement for all your elements, but using jsx is much easier.

- difference between an element and a component
    - an element is somehting that is created by jsx as an object
    - a component is a function that returns an object. components are functions of elements.


- props (properties)
    - how do you pass a value from parent to child? props.
    - what about form child to parent?
        - pass a function prop.
        - pass a function from parent to child via props. and then that child would call that function, and that function being called would be passed up the the parent.
    - what is prop-drilling?
        - drilling props down a bunch of different components. from grandparent to parent to child etc. continually passing props down via multiple levels
    - can you modify props?
        - no. you can't. props are read-only.
        - the reason is because functions are supposed to be pure components.
        - all react components must act like pure functions with respect to their props. they always return the same output for the same input.

- state and lifecycle
    - what is the difference between props and state?
        - both are js objects. both hold information that influences what will be rendered, but props get passed to a component (kind of like function parameters), but state is mananged within a given component. its kind of like variables declared within a function. they are scoped within that function. state is local to a given component. you cannot access state outside a given component unless you pass it with props. it is completely inside, scoped and local, within a given component.

    - what is the difference between state in a class component vs state in a function component?
        - state in a class component, you use a function called this.getState(). this is something that is attached to a class object. the component in a react class is an object and the state is somehting that persists across that class component.
        - state in a function component is something that is recalled multiple times. because a fucntion component isn't an object that persists over time, where its something that you manipulate. it is something that is recalled over time, every single time state changes. that is the high level answer
        - state persists in a class component, state is recalled in a function component.
    
    - what is the component lifecycle? 
        - state kind of controls the component lifecycle
        - mounting (first appearance)
            - render, componentDidMount
        - updating (because state has changed)
            - render, componentDidUpdate
        - unmounting (remove event listener, etc)
            - componentWillUnmount

    - how do you update the lifecycle in function components?
        - use the hook useEffect to update state

- effects
    - what parameters does useEffect take in?
        - a function and a dependency array that determines when the function (the effect) will be run.
    - when does the useEffect function run?
        - on mount, whenever things update - simple answer
        -  complex answer depends on the dependency array
            - [] -> runs on mount
            - [variable] -> runs on mount and when the variable changes
            - no array -> runs on mount and on every state change.
    - what is the useEffect function's return value?
        - the return value is called a cleanup function. and that cleanup function is something that cleansup any event listeners, any fetch cancellation types of things. it says 'hey the component is about to unmount'
        - you can update state variables etc inside the function, but the cleanup function is called when the component is about to unmount.
        - useEffect is very useful because it can cover every single one of the lifecycle methods in a much more concise way. it is very powerful.

- refs
    - what is the difference between refs and state variables?
        - they are very similar  both objects that can contain values.
        - but state variables are soemthing that can trigger a rerender, but refs don't. refs have a value that persist across renders - they can just hold on to something you might need.
    - when is the best time to use a ref?
        - great for library authors - where info remains stagnant. it literally says in the react documentation to not overuse them.
        - managing focus or media
            - use a ref to focus the input element on a modal?
        - triggering animations
            - somehting that is imperative and not state-driven
        - integrating with DOM libraries
            - ref gives 3rd party libraries something to grab on to for the DOM since the virtual DOM does not.
    - what is the proper way to update a ref in a function component?
        - if you need to update a ref, useEffects to do so.

- context 
    - what is the difference between Context API and prop drilling? (this is a very common question)
        - first of all, prop drilling is for explicitly stating props and values that a given child component can get.
        - meanwhile, the context API implicitly states what values a given child component can have. witht the context api, you define something at the top level and put those values in at the top level, and then anything inside that component tree, anything that is within a given context at the top has access to the values that you give it.
        - props need to be passed from compoennt to component to component. with this, you know exactly where certain values are being passed at any give time,  but you those values also can be manipulated on accident.
        - but with a context api, beacuse the values are defined at the top level and can be access/manipulated at any level of the tree, you might have some unncessary rerenders. something to be aware of.
    - when shouldn't you use the context api?
        - you shouldn't overuse it. be discernign to avoid rerenders. 
        - i would only put what's absoltuely necessary at the top level of my application with context. everything else i would just make more context apis if they need to be shared, otherwise props are a perfectly good way of sharing different state values and refs.
        - context is really useful for things like authentication or a website theme or something that really needs to be shared across an application tree, but itss not something you need to keep track of a lot of different clicks or something.
        - this is somethign that came out of redux popularity but led to a lot of rerenders.

- misc.
    - what is a fragment?
        - kind of nothing. they're containers to hold onto different elements. with react you need to return only one element every single time - to avoid 10 layer divs and how that can mess up design elements. makes sure you're only returning one individual thing.
    - when should you used a class based component vs function components?
        - class components are becomign outdated and function components are the future of react. all the new features of react are geared toward function based components. 
        - the only thing you absolutely need to use class based components for is 'error boundaries'. 
            - error boundaries are react components that catch javascript errors anywhere in the child component tree. they log those errors, they display a fallback UI instead of the component tree that crashed. 
            - they catch a lot of errors during rendering and in lifecycle methods and in constructors of the entire tree below them. they're pretty neat, but you need class based components for them because there aren't any hooks geared for them yet.
    - what is a higher ordered component (HOC)?
        - this is a function that takes IN a component and it returns a new component. it is used for reusing component logic and it isn't a react API thing its just a pattern that emerged within react.
    - what is a portal?
        - a way to render children into a DOM node that exists outside of the DOM hierarchy of the parent component. it can live anywhere in the DOM tree and you most often see it in UI components like modals where the modal lives separately from the entire tree of different components containing each other.
    - what are controlled and uncontrolled components?
        - uncontrolled components are input values - some sort of user manipulated component. something that the user controls and not that react controls. 
        - controlled components are a solution to the potential discrepancies ebtween the virtual DOM and the real DOM ( if you had jQuery and React on the same site, for instance). where you have a given input and react controls it - it controls the state changes happening in it and react to those state changes. it is the thing that contains that component. jquery can't touch it, and react can prevent a user from interacting with it.

    - convert from a class based component to a function based component:
    