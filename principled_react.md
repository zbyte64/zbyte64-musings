# Predictable Components use explicit display flags

Use explicit properties to control display modes.

```javascript
Card.propTypes = {
  highContrast: PropTypes.bool,
  darkMode: PropTypes.bool,
  hover: PropTypes.bool,
  flip: PropTypes.bool
};
```

## Replaces

- Checking the `className` to toggle display features.
- Checking key or index to alternate display features.

## Why?

This makes controlling the behavior from the outside obvious.
Inside the component the explicit variable names make it easier to follow what
each mode entails.

# Readable Components have intermediate variables

- Redundant decisions should be moved into their own variables.
- Larger expressions in the markup should serve to draw attention to important junctions
- Use descriptive variable names

```javascript
const listItems = children.map((x, i( => {<li key={i}>{x}</li>})));
```

## Why?

Encourages your component to read like a recipe.
A component may have allot of dependencies that has supporting logic.
These preparatory steps are required but the specifics are not necessary for understanding the component as a whole.
This prep-work can float above the return where everything gets packaged together.

# Reusable Components support className

Components should accept `className` as a property.

```Javascript
// styled() wraps a component and injects css via className property
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

## Responsibilities

Parent components should control placement with:

- width, height
- grid-area
- flex
- margin

Components should exclusively control their own:

- padding
- internal margins
- color
- hover
- fonts
- grid-template

## Replaces

- any other property for injecting CSS at the container level

## Why?

Class names is already a robust pattern used everywhere.
Separating the concerns in this manner makes the component more predictable in other contexts.

# Understandable Components use semaphores

Use a datastructure to store classNames or other state dependent artifacts.
Map datastructure artifacts to component properties using (state) variables to navigate the structure.

```javascript
const classNameSemaphore = {
  true: ["primary-bg white", "light-bg"],
  false: ["light-bg", "primary-bg white"]
};

const className = _.get(classNameSemaphore, [primary, hover], "");
```

## Replaces

- Nested if/else statements
- Chained ternary expressions

## Why?

Complex decision rules are often better represented as data than a series of conditionals.

## Why Not?

- Not necessary if the decisions are one level deep.
- May create adhoc Domain Specific Language

# Use factories to delegate dependencies

Use functions to generate intermediate markup.

```javascript
function statusDisplay(entry) {
  switch(entry.state) {
    case "PENDING":
      return <Loading percentage={entry.percentageComplete}/>;
    case "SUBMITTED"
      return <Next receipt={entry.id}/>;
    case "ERROR":
      return <Error message={entry.msg}/>;
  }
}
```

## Replaces

- Complex expressions in the return markup
- Proxy components that encode business logic

## Why?

- A function that returns components is simpler then a new component
- Moves implementation logic out of the main markup

## Why Not?

- Adds interruption to reading flow
- Avoid factorizing entire component

# Modifiable Components accept other Components

- children property for single slot inclusion
- explicit properties for specifying slots

```javascript
<Dashboard header={<TopMenu user={user} />} footer={<Footer />}>
  <h1>Welcome</h1>
</Dashboard>
```

## Replaces

- copying entire component trees
- passing in CSS
- CSS selecting children with classNames

## Why?

Composition via React properties gives direct control over styling and behavior.

## Why Not?

The parent component may require certain behaviors of it's child components. Ideally the components passed in via properties would be wrapped in a component that adds the needed functionality, but additional coordination maybe required, like signaling a hover visual state. Anyway we look at it, this pattern tends towards imposing additional constraints on it's components.
