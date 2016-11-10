### React Patterns

1. ##### Stateless functions

```jsx
const Greeting = (props, context) =>
  <div style={{color: context.color}}>Hi {props.name}!</div>
  
Greeting.propTypes = {
  name: PropTypes.string.isRequired
}
Greeting.defaultProps = {
  name: "Guest"
}
Greeting.contextTypes = {
  color: PropTypes.string
}  
```

2. ##### JSX Spread attributes

```jsx
const FancyDiv = props =>
	<div className="fancy" {...props} />

<FancyDiv data-id="my-fancy-div">So Fancy</FancyDiv>  
```

3.    ##### Destructuring arguments

```jsx
const {color, ...otherProps} = this.props

const Greeting = ({ name, ...props }) =>
  <div {...props}>Hi {name}!</div>
```

4. ##### Conditional rendering

If block

``` jsx
{condition && <span>Rendered when `truthy`</span> }
```

Unless block

```jsx
{condition || <span>Rendered when `truthy`</span> }
```

Ternary operator

```jsx
{condition
  ? <span>Rendered when `truthy`</span>
  : <span>Rendered when `falsey`</span>
}
```

5. ##### Array as children

```jsx
<ul>
  {arrayOfMessageObjects.map(({ id, ...message }) =>
    <Message key={id} {...message} />
  )}
</ul>
```

6. ##### Proxy component

write a higher level component to proxy `props` to a lower-level `button` component.

```jsx
const Button = props =>
  <button type="button" {...props}>
```

We can use `Button` in place of `button` and ensure that the `type` attribute is consistently applied everywhere.

```jsx
<Button />
// <button type="button"><button>

<Button className="CTA">Send Money</Button>
// <button type="button" class="CTA">Send Money</button>
```
7. ##### Inline event handlers

```jsx
<div onClick={() => console.log('clicked here')}
```

