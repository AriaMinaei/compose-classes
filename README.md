# Compose css classes

A small utility function to make react components that use css modules to have extensible styles.

## Example

```typescript
/**
 * Foo.tsx
 **/
import * as css from './Foo.css'
import composeClasses from 'compose-classes'

type Props = {
  css?: Partial<typeof css>
}

export const Foo = (props: Props) => {
  const classes = composeClasses(css, props)

  return <div {...classes('container')}></div>
}

/**
 * Bar.tsx
 **/
import * as css from './Bar.css'
export const Bar = () => {
  // a div will be rendered that has both the container class
  // from Foo.css and also the fooContaienr class from Bar.css
  return <Foo css={{container: css.fooContainer}} />
}
```

```css
/**
 * Foo.css
 **/
 .container {
   background: black;
 }

 /**
 * Bar.css
 **/
 .fooContainer {
   color: white;
 }
```

Look at `src/index.test.ts` for more examples.