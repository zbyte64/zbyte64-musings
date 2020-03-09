# Readable Components have simple properties

* Redundant decisions should be moved into their own variables.
* Larger expressions in the markup should serve to draw attention to important junctions
* Descriptive variables are more readable than ternary expressions.

## Why?

The more syntax, spaces, and variables one views in a single glance the more effort is required in understanding a behavior.

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


## Why?

Class names is already a robust pattern used everywhere.
Seperating the concerns in this manner makes the component more predictable in other contexts.


# Predictable Components use explicit display flags

Display modes should be controlled with explicit properties.

## Replaces

* Checking the className to toggle display features.
* Checking key or index to alternate display features.

## Why?

Explicit functionality should be interfaced explicitly.

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
* Chained ternary expressions

## Why?

Concentrates the behavior of selecting visual state and puts it outside the markup.
Not necessary if the decisions are one level deep.


# Use factories to manage dependencies

A function that returns components and simpler then a new component.


```javascript
const listItems = children.map((x, i( => {<li key={i}>{x}</li>});
```

## Replaces

* Inline expressions in the return markup
* Proxy components that encode business logic

## Why?

Encourages your component to read like a recipe.
A component may have allot of dependencies that has supporting logic.
These preperatory steps are required but the specifics are not necessary for understanding the component as a whole.
This prep-work can float above the return where everything gets packaged together.


# Moddable Components accept other Components

* children property for single slot inclusion
* explicit properties for specifying slots

```javascript
<Dashboard
  header={<TopMenu user={user}/>}
  footer={<Footer/>>
    <h1>Welcome</h1>
</Dashboard>
```

## Replaces

* copying entire component trees
* passing in css
* css selecting children

## Why?

This is a composition pattern using react properties.
Composition is favored over making a new class or function.

