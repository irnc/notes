* http://sailsjs.org/
* Get Started
* `npm i sails -g`
* `sails new telephone`
* http://localhost:1337/
* `sails help`
* `sails generate`... something
* `sails generate --help` of no help
* `sails help generate`
* `sails generate api phone` into the deep waters
* `http://localhost:1337/phone` 404, so no live reload
* Ctrl+C on lifted `sails lift`, `sails lift` again

```
info: Starting app...

-----------------------------------------------------------------

 Excuse my interruption, but it looks like this app
 does not have a project-wide "migrate" setting configured yet.
 (perhaps this is the first time you're lifting it with models?)
 
 In short, this setting controls whether/how Sails will attempt to automatically
 rebuild the tables/collections/sets/etc. in your database schema.
 You can read more about the "migrate" setting here:
 http://sailsjs.org/#/documentation/concepts/ORM/model-settings.html?q=migrate

 In a production environment (NODE_ENV==="production") Sails always uses
 migrate:"safe" to protect inadvertent deletion of your data.
 However during development, you have a few other options for convenience:

 1. safe  - never auto-migrate my database(s). I will do it myself (by hand) 
 2. alter - auto-migrate, but attempt to keep my existing data (experimental)
 3. drop  - wipe/drop ALL my data and rebuild models every time I lift Sails

What would you like Sails to do?

info: To skip this prompt in the future, set `sails.config.models.migrate`.
info: (conventionally, this is done in `config/models.js`)

warn: ** DO NOT CHOOSE "2" or "3" IF YOU ARE WORKING WITH PRODUCTION DATA **

prompt: ?:  error: Error: The hook `orm` is taking too long to load.
Make sure it is triggering its `initialize()` callback, or else set `sails.config.orm._hookTimeout to a higher value (currently 20000)
  at [object Object].tooLong [as _onTimeout] (/home/pavel/.nvm/v0.12.2/lib/node_modules/sails/lib/app/private/loadHooks.js:92:21)
  at Timer.listOnTimeout (timers.js:110:15)
```
