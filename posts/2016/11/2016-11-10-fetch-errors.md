# The most concise error from Fetch API

[Fetch Standard][fetch] does not define error messages, just a type of an error,
which should be `TypeError` for all thrown errors.

TK Why Fetch Standard introduces concept of response of _network error_ type?

[fetch]: https://fetch.spec.whatwg.org/

Following properties (and only them) could be seen on error rejected from
fetch promise:

```js
{
  message: "Failed to fetch",
  stack: "TypeError: Failed to fetch"
}
```

## Reasons of a `TypeError`

> A fetch() promise will reject with a TypeError when a network error is
encountered, although this usually means permission issues or similar — a 404
does not constitute a network error, for example. An accurate check for a
successful fetch() would include checking that the promise resolved, then
checking that the Response.ok property has a value of true.

[ref](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

- https://gauntface.com/blog/2015/02/11/fetch-is-the-new-xhr suggests CORS
- in my case it was `net::ERR_CONNECTION_REFUSED` due to no one listening on
  server side, e.g. server not running

## Rationale for concise error message and no additional information

Fetch Standard does not rationalize concise error usage. It could be due to
security concerns, to prevent network probing from exploited XSS.
