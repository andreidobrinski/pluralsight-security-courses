# Software and Systems Security for CompTIA CySA+

[Link to course](https://app.pluralsight.com/library/courses/software-systems-security-comptia-cysa-plus/table-of-contents)

## Software Development Lifecycle (SDLC)

- Goes through stages: Planning, Requirement analysis, Design, Implementation, Testing, Maintenance
- multiple people involved an each step: devs, designers, testers, PMs etc

Benefits of SDLC

- documentation
- better picture of what needs to be done
- tool for maintenance
- creates goals and for each step in the process
- allows for better review of work
- produce a tangible item
- gives direction for next phase

SDLC Phases (8):

1. Planning

- creating a blueprint for what needs to be built
- done by senior members and some customers
- input from different departments
- plan basic project approach

2. Requirement

- software requirement (internal/external)
- hardware requirements
- external sources (data, partners etc)
- where is the data being stored?
- how is traffic being transmitted?
- how it access granted to users?

3. Design

- risk analysis, look into threats and vulnerabilities potentially being exposed
- functional specifications: includes interface requirements (do we allow alphanumeric inputs, dates before the current date)
- workflow (UX)
- audit trail for every update on the database

4. Implementation

- look at resources from known resource environment (what code is being ran in the background)
- understand the connections between resources, internal and external

5. Testing

- look at the infrastructure the way an attacker would look at the infrastructure

6. Deployment

- how is the software being distributed?
- is the deployment mechanism secure?

7. Maintenance

- OS updates
- patches or 3rd party updates

8. End-of-life

- steps to removing the software
- effects on backend resources
- disable service accounts
- documentation helps to disassemble what was built

Code-and-fix

- aka not having a plan
- fix problems as they occur
- planning and deployment optional

Waterfall

- each phase happens in a linear sequential order
- when requirements are well documented
- when technology is understood and isnt dynamic
- when Ample resources available and expertise

Agile

- not a model, made up of values and principles
- focus on individuals and interactions
- working software
- customer collaboration
- responding to change (welcome changing requirements)
- working software is a measure of progress

Iterative

- new piece of software after each iteration
- goes thru design & dev > testing > implementation

Spiral

- combines waterfall with iterative
- incremental releases
- 4 phases: identification, design, build, risk analysis
- each pass through the phases is one spiral

## Code Review

Manual code review

- self
- teammate
- security analytist

Automated code reviews

3 outlines for CR

1. Scope

- what types of code is reviewed?
- what are you looking for?
- need to understand business logic as well

2. Categorize

- categorize how high of a priority the fix should be

3. Recommendation

- get rid of false positives from false positives
- document vulnerabilities
- include mitigation steps

Types of reviews

- static code vs dynamic code
  - static looks at source code in the editor
  - dynamic looks at running code
- manuar peer review
  - reviewed by developers other than the original coder
- user acceptance testing (UAT)
  - beta testing
- fuzz testing
  - tests for bugs and vulnerabilities
- fault injection
  - sends unexpected data to program
- mutation testing
  - related to fuzzing. makes small modifications to the program itself.
  - types of errors typical to developer mistakes
- load testing
  - simulates full application load
  - searches for limitations
  - cloud apps are harder to load test
- security regression
  - tests that changes made dont introduce new issues
- formal method
  - uses a mathematical model to prove that the system works

Intercept proxies

- combines a proxy server with a gateway
- sits between the browser and the internet connection
- controls time between submission to browser and data received

Burp Suite

- sets up as a proxy on the web browser
- allows you to pull additional data from a web server

OWASP ZAP

- also runs intercept proxies
- runs tests and finds issues
- provides solutions to issues, as well as references

Reverse Engineering

- extracting of code from binary executables to work out how it was programmed
- decomposing the code:
  - use a disassembler
  - use a decompiler
  - use debuggers
- obfuscating the code:
  - randomizes the names of variables
  - removes comments
- reverse engineering labs

## Coding Best Practices

Input Validation

- perform all validation on a trusted system
- ID all data sources (trusted/untrusted)
- use a centralized input validation routine
- use proper character sets (UTF-8)
- encode data using character set
- failures should result in system rejecting
- confirm client data before processing
- verify that headers contain only ASCII
- validate data from redirects
- validate for expected data types, range, and length

Output Encoding

- encode only on a trusted system
- testing routing for each outbound encoding
- encode all characters
- sanitize all queries and commands

Auth

- require auth for all pages and resources except public ones
- forced auth on trusted system
- use centralized implementation controls
- move auth logic away from resource being requests
- use a redirect to and from the auth control
- auth should fail securely
- salted hashes for passwords, writable only by the application
- pwd hashing on trusted system
- generic error responses
- use only HTTP post
- enforce complexity (pwd length) requirements
- pwd entry should be obscured
- disable account after wrong passwords (5) to discourage brute force
- reset questions should be custom
- send reset questions only to pre-registered links
- make users change their temp password
- notify users when password reset is requested
- prevent password recycling
- passwords must be one day old before a reset
- show user sessions to the user
- change vendor default password
- reauth before critical operations
- 2fs for high value accounts

Session Management

- session ID on a trusted system
- vetted algorithms for random session id
- logout should fully terminate session
- logout should be from all auth pages
- short session inactivity
- no persistent logins
- close session before another login
- no concurrent logins
- hide sessions ID's from urls
- new session ID if changing from HTTP to HTTPS. ideally keep HTTPS
- "secure" for cookies. use HTTP-only cookies

Access Control

- single site-wide component to check access control
- access controls should fail securely
- enforce auth controls on every request
- authorized users should only have
  - limit access to files/resources that they need
  - access to protected URLs
  - limit access to services
  - limit application data access
  - state data must be stored on the client
  - enforce app logic to comply with business rules
  - limit the number of transactions that a user/device can perform in a time period
  - retire unused accounts
  - create an access control policy

Cryptographic Practices

- modules should fail securely
- random number generator should be compliant FIPS 140-2
- policy and process for key management

Error handling

- dont disclose sensitive data in error responses
- dont display stack trace
- use generic errors
- error handling should deny access by default

Data protection

- restrict users to the least privilege that they need
- purge data that is not longer needed
- remove comments from production code
- no sensitive info on HTTP GET
- disable client side caching
- support data removal if asked

Communication Security

- use TLS. valid certificates.
- dont fall back to insecure connection
- tls for external connections
- single tls implementation
- force character encodings
- filter params in HTTP header

System Configs

- use latest versions
- disable directory listings
- define which HTTP methods the app supports
- clean HTTP header response from OS data
- isolate dev from prod environments

Database Security

- strong typed parameterized queries
- input validation/output encoding
- force strongly typed operations based on expected data types
- no hard-coded connection strings
- shutdown the connection if it's not being used
- disable db functionality that isn't used

File Management Security

- auth before upload
- only expected types of files to upload
- check files headers in addition to extension
- turn off execution privileges on uploads
- whitelist of allowed file types

Memory Management

- check that buffer size is as large as specified
- check the buffer boundaries
- dont rely on garbage collection
- free up RAM

## Cloud Computing

Service-Oriented Architecture and Microservices

- close is mapped to business workflows
- can contain subservices
- self-contained. doesn't need to rely on the state of any other service

API connectivity issues

- SOAP (Simple Object Access Protocol)
- REST (Representational State Transfer), uses HTTPS
- API keys must be secured
- Communications should use HTTPS

Security Assertion Markup Language (SAML)

- user auth, entitlement, attributes
- SSO
- auth is contained in assertions
- binding communications

Infrastructure as Code

- eliminate snowflake systems
  - a config or build that is different than any other
  - leads to security issues
  - Microsoft Desired State Configuration (DSC)
