# Predictable Components use explicit display flags

Use explicit properties to control display modes.
This makes controlling the behavior from the outside obvious.
Inside the component the explicit variable names make it easier to follow what
each mode entails.

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
- Inferring display features from key or other conceptually different properties.

# Readable Components have intermediate variables

Move redundant decisions into their own variables with descriptive names.
Leave larger expressions in the markup to draw attention to important junctions.
This encourages your component to read like a recipe.
Requirements in the beginning, details in the middle, returned results at the end.

```javascript
const listItems = children.map((x, i( => {<li key={i}>{x}</li>})));
```

# Reusable Components support className

Components should accept `className` as a property.
Other tools, like emotion, use `className` to attach other properties like `css`.
Additionally, `className` allows handing off placement concerns to the parent component.

```Javascript
// styled() wraps a component and injects css via className property
// child component definition
const ResponsiveCTA = styled.div`
    padding: 20px;
`;
// we can add styles at rendering time
const renderedCTAWithMargins = <ResponsiveCTA css={{marginBottom: "20px"}}>Click Me</ResponsiveCTA>


// or extend as a new component
const LeftCTA = styled(ResponsiveCTA)`
    float: left;
    margin: 30px 50px 30px 0px;
  `,
  RightCTA = styled(ResponsiveCTA)`
    float: right;
    margin: 30px 0px 30px 50px;
  `;
```

The following are general rules for splitting CSS logic between the component itself and the parent.
If you need the component in another context but this isn't enough, consider forking or supporting composition.

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

# Understandable Components use semaphores

Use ternaries or datastructure as semaphores to route state to display artifacts.
Complex decision rules are often better represented as data than a series of conditionals or even a single if/else statement.

```javascript
const classNameSemaphore = {
  true: ["primary-bg white", "light-bg"],
  false: ["light-bg", "primary-bg white"]
};

const className = _.get(classNameSemaphore, [primary, hover], "");
const border = hover ? "primary" : "secondary";
```

# Use factories to delegate dependencies

Use functions to encapsulate a series of decisions generate intermediate markup.

```javascript
// decide which component to display along with properties
const [loadState, setLoadState] = useState(true);

function statusDisplay(entry) {
  if (loadState) return null;
  switch (entry.state) {
    case "PENDING":
      return <ProgressBar percentage={entry.percentageComplete} />;
    case "SUBMITTED":
      return <Invoice receipt={entry.id} />;
    case "ERROR":
      return <Error message={entry.msg} />;
  }
}
```

# Modifiable Components accept other Components

Most components we build should not be modifiable.
But components we see often or as part of a style guide should have a flexible code analogue available to the developer.
Composition via React properties gives direct control over styling and behavior.
Use the `children` property to accept a "main" component to display inside another component.
For multiple sections use an explicit property for each section to be displayed inside the component.

```javascript
<Dashboard header={<TopMenu user={user} />} footer={<Footer />}>
  <h1>Welcome</h1>
</Dashboard>
```
