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


- function components are the future of react - away from class based and life cycles
