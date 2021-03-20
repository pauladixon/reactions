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

            