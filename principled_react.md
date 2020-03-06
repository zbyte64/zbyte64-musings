# Readable Components have simple properties

* Redundant decisions should be moved into their own variables.
* Larger expressions in the markup should serve to draw attention to important junctions
* Descriptive variables are more readable than ternary expressions.


# Reusable Components support className

Allows parent components to control placement.
* width, height
* grid-area
* flex
* margin

Components should exclusivly control their own:
* padding
* internal margins
* color
* hover
* fonts
* grid-template


```Javascript
// child component definition
const ResponsiveCTA = styled.div`
    padding: 20px;
`;


// parent component wraps for placement
const LeftCTA = styled(ResponsiveCTA)`
    float: left;
    margin: 30px 50px 30px 0px;
  `,
  RightCTA = styled(ResponsiveCTA)`
    float: right;
    margin: 30px 0px 30px 50px;
  `;
```

## Replaces

* any other property for injecting css at the container level

# Predictable Components use explicit display flags

Display modes should be controlled with explicit properties.

## Replaces

* Checking the className to toggle display features.
* Checking key or index to alternate display features.


# Understandable Components use semaphores

Use a datastructure to store classNames or other state dependent artifacts.
Map datastructure artifacts to component properties using state variables to navigate the structure.


```javascript
const classNameSemaphore = {
  true: ["primary-bg white", "light-bg"],
  false: ["light-bg", "primary-bg white"],
};

const className = classNameSemaphore[primary][hover];
```

## Replaces

* Nested if/else statements 
* Ternary expressions


# Use the Factory pattern

A function that returns components and simpler then a new component.

## Replaces

* Proxy components that encode business logic
* Inline component list generation in markup

