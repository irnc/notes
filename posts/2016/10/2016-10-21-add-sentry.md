# How to add Sentry to client side?

- sign up at https://sentry.io/
- follow instructions
  - in my case I used webpack, so I run `npm i -S raven-js`
  - add `Raven.config().install()` call before own code
- see uncaught exceptions reported to Sentry

# Sentry is amazing!

Right from the start it captures uncaught exceptions and reports them together
with _breadcrumbs_, which are a log of console messages and user actions that
lead to an exception.
