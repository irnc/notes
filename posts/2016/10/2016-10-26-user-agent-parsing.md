## Solution

Use https://npms.io/.

My choice as of October 2016 is `npm install ua-parser-js`.

## Overview

- `express-useragent`
  - https://github.com/biggora/express-useragent
  - solo implementation
- `useragent`
  - https://github.com/3rd-Eden/useragent
  - optimized `ua-parser`
- `ua-parser`
  - https://www.npmjs.com/package/ua-parser
  - https://github.com/tobie/ua-parser/tree/master/js
    - or https://github.com/ua-parser/uap-ref-impl?
    - as of 2016, not updated since 2014
  - based on regexps from BrowserScope
  - old derivatives
    - Ruby
      - https://github.com/yabawock/useragent_parser
    - JavaScript
      - `useragent-parser`
        - https://www.npmjs.com/package/useragent-parser
        - https://github.com/koenpunt/node-useragent-parser
- `useragent_parser`
  - https://github.com/koudelka/node-useragent_parser
  - https://www.npmjs.com/package/useragent_parser
  - no use
- `user-agent-parser`
  - https://www.npmjs.com/package/user-agent-parser
  - https://github.com/faisalman/ua-parser-js
