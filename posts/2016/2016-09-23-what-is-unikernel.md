I searched and read following pages, but they wasn't of any help to me.

- https://en.wikipedia.org/wiki/Unikernel
- https://blog.docker.com/2016/05/docker-unikernels-open-source/
- https://blog.docker.com/2016/01/unikernel/

Latest one given me a hint to http://unikernel.org/resources/. Which opened a
treasure http://unikernel.org/files/2014-cacm-unikernels.pdf.

## Notes from the article

> Functional programming has an emphasis on supporting abstractions that make
it easier to track mutability in programs, and previous research has shown that
this need not come at the price of performance.

---

MirageOS integration with Citrix XenServer.

- http://gazagnaire.org/pub/SSGM10.pdf

---

How Elm ideas correspond to MirageOS SAT solving?

---

> Libraries in MirageOS are designed in as functional a style as possible: they
are reentrant with explicit state handles, which are in turn serializable so
that they can be reconstructed explicitly.

---

Check out https://mirage.io/, which is served by unikernel. Note: 38 seconds
to load as of September 23, 2016 (maybe under a heavy load).
