# Bare Bones

- setup Git repository
- use `create-react-app` to create application skeleton
- use `yarn`
- add needed packages: `redux`, `react-redux`, `react-router`, `storybook`

# Presentational Components

Prerequisites:
- graphical design, mockups or wireframes

Goals:
- get into business domain language
- breakdown graphical design into named components

Steps:
- put presentational components into `components/`
- route to presentational components directly (for now)
- create dumb presentational components, i.e. with data inside `render`

Deliverables:
- dumb presentational prototype deployed to server

# Container Components

Goals:
- design and implement data shape on a component level

Steps:
- put container components into `containers/`
- create _disconnected_ container components with mocked data
  - i.e. with mocked data in `mapStateToProps` instead of data from `state`
- use `storybook` for showcasing different states of components
- change dump presentational components to receive data via props

Deliverables:
- living Storybook showcasing components in different states

# State and Behavior

Goals:
- design and implement state shape at Redux level
- get into actions and behavior from business domain

Steps:
- think about shape of the state
- break it down into composed reducers
- connect container components to state

Deliverables:
- functioning prototype
