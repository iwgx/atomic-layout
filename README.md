A single component to distribute spacial relation between your atom components.

## Motivation

[Atomic design](http://bradfrost.com/blog/post/atomic-web-design) is outstanding. If this is the first time you hear about it, go check it out and don't forget to show it to your designer as well.

Implementation of atom components is straightforward. But when it comes to composing molecules how do you handle the relation between the atoms? Most likely, you are creating extra CSS to change position or add spacing to the atoms which are under a specific molecule. Not only that makes you write more CSS, but it also contradicts the idea of atom being independant, reusable, predictable.

**What if there was a single layer above the atoms that could distribute spacial relation to atoms without actually affecting them?** Well, this is what this repository is about.

## Technology

We are using a jaw-droppingly powerful (and standardized) [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) and combining it with the simplicity and flexibility of [React](https://reactjs.org/). You can depict this library like an easier way to declare and maintain CSS Grid in your React application.

## Getting started

```jsx
import React from 'react'
// import the "Layout" from the library
import Layout from 'atomic-layout'

// declare templates ("grid-template-areas")
const templateMobile = `
  'thumbnail'
  'heading'
  'subheading'
`

// including for different screen sizes
const templateDesktop = `
  'thumbnail heading'
  'thumbnail subheading'
`

export default class Card extends React.Component {
  render() {
    return (
      {/* Configure the Layout */}
      <Layout template={templateMobile} templateSmUp={templateDesktop}>
        {/* Get the components out of your grid areas */}
        {({ Thumbnail, Heading, Subheading }) => (
          <React.Fragment>
            <Thumbnail>
              <img src="foo.png" />
            </Thumbnail>
            <Heading>
              <h4>Juicy fruits</h4>
            </Heading>
            <Subheading>
              <p>Healthy mind in a healthy body.</p>
            </Subheading>
          </React.Fragment>
        )}
      </Layout>
    )
  }
}
```

## Support

See the [Support table](https://caniuse.com/#feat=css-grid).
