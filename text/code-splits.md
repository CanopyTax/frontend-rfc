# Code splits

## Squad vs Chapter vs Frontend tribe
All squads must adopt a policy of having as small as possible initial entry file by aggressively code splitting.

## Definition
Code splitting is a methodology by which a large bundle of code can be chunked/divided/split into multiple smaller bundles that can be dynamically loaded at runtime.
Many modern web development patterns use a bundler (webpack, parcel.js, etc) that takes multiple files, dependencies, or even languages and compiles them into a single executing javascript bundle.
Bundles can get large over time so it's good to get a head of the problem and start "splitting" your bundle.

## Reason for decision
Many of our projects need exported functions from another project. When project A relies on project B and project B doesn't aggressively code split, significant amounts of code must be loaded to use the small feature/method from project B.
A real world example: Primary-nav imports methods that create things (contacts, tasks, etc). If contacts doesn't have a small entry file and aggressively code split out the dashboard and other features then those features all have to be loaded in memory before we can show the create contact modal.

## How to best accomplish goal
- Entry file contains no statically imported components of functions
- Entry file has exported methods that return a promise to get a "split" method via dynamic module imports
- When in React use react lazy to import a component

### Example
```js
// contacts-ui.js
import React from 'react'
import ReactDom from 'react-dom'
import singleSpaReact from 'single-spa-react'

const lifecycles = singleSpaReact(...)
export mount = lifecycles.mount

export function getAddEditContactModal() {
  return import('./add-edit-contact-modal').then(...)
}

```

```js
// primary-nav.js
// global-add-button.js
import React, {lazy} from 'react'
const AddEditContactModal = lazy(
  () => System.import('contacts-ui')
    .then(cui => cui.getAddEditContactModal())
)

export function globalAdd(props) {
  const [ showContactModal, setShowContactModal ] = useState(false)
  return (
    <div>
      {
        showContactModal && (
          <AddEditContactModal />
        )
      }
    </div>
  )
}

```
