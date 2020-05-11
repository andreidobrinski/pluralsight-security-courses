JavaScript Security

[Link to course](https://app.pluralsight.com/library/courses/play-by-play-javascript-security)

Logging someone into the site

- using auth tokens
- persists across refresh

Cookies for auth token

- can choose to expire them
- http only cookies can't be accessed by a client script
- flag cookies as http only so that they're resilient to XSS
- can't use this with async services
- not the best way to store auth

Auth in session storage

- can access this with client scripts
  - can be used with async services
- doesn't get automatically sent with every request like a cookie
- valid until the last window of chrome is closed
- downside: can't control the time that it'll expire like a cookie
- vulnerable to XSS
  - because session storage is just a global object

Local storage

- similar to session storage
- persists for the lifetime of the browser
  - or until the user clears all cache
- no expiration date like session storage
- need to manually remove token on logout

Service workers

- available in all big browsers
- runs in the background of the web application
- runs even when the browser is closed
- used to intercept network requests and proxy them to work offline with cached data

CORS

- cross origin resource sharing
- allows requests to come from a known source, but not other sources
- cache api is only available on HTTPS

Third-party libraries

- need to be aware of libraries used in production
- if a library gets hacked, it could potentially be shipping compromised code in projects that depend on it
- big difference between pulling in a version on a library (locked in time) vs pulling in a script tag that is subject to change

Sub Resource Integrity - SRI

- an integrity tag that hashes a version of a library
- hashes have to match for the browser to use the library
- if the library has been changed, hashes wont match

Content Security Policy - CSP

- whitelist for addresses that can use either scripts or images
- eg if you add something.com to your CSP but the script changes to pull a script from another site, the other site won't be allowed to run the script

Sonarwhal

- linter for how the application will run
- looks for hosting and dependencies

Misspelled versions of popular packages that inject malicious code

- accidentally npm installed with typo

Client-side validation is good but it can't be the only validation

- need server-side validation to go along with it
- cant necessarily trust information that's coming from the browser
