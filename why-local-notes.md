# Cloud is not reliable

Google Drives could fail from time to time. Once in a while it responded with
_The server encountered an error. Please try again later._ for quite a long
time.

The root cause was that some application assets wasn't served properly,
responding with 502 status code.

```
502. That’s an error.

The server encountered a temporary error and could not complete your request.

Please try again in 30 seconds. That’s all we know.
```
