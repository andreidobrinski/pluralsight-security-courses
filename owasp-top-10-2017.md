# OWASP Top 10

[Link to course](https://app.pluralsight.com/library/courses/play-by-play-owasp-top-ten-2017)

Intended as an awareness piece, not a standard.

First started in 2003

- updated every 3-4 years after that

Has recently changed a lot to adapt to many new and popular JS frameworks

- jQuery, Angular, React, Vue

Used to not be very data-driven but has since changed.

OWASP Top 10 List

1. Injection

- one impact factor away from making it number 4
- dropped from 20% in 2007 to less than 5% today
  - impact is still severe
- frameworks are saving developers from SQL injections
- XSS is down because it makes is harder to do the wrong thing

2. Broken Authentication

- was still #2 is 2013
- would be a1 because humans are bad as passwords
  - password reuse is a big factor
- unlikely that the majority of the internet will not adhere to complex, unique passwords
- need to know and prevent when bots are trying 1000's of valid accounts
  - recaptcha can be good for this
  - even invisible recaptcha
    - smaller barrier to entry
    - user doesn't need to do another action
- need to help users choose better password
- password rotation is not a good policy
  - computers have gotten faster at running through more possible combinations to guess

3. Sensitive Data Exposure

- moved from position 6 to position 3
  - primarily because of equifax
- number of breaches went up and impact went up
- it's about GDPR
- it's also a people issue: protecting people's data
- data becomes sensitive when grouped
  - phone # or email alone is not sensitive
  - phone with email with home address becomes sensitive

4. XML External Entities (XXE)

- was not previously in top 10
- it's not tested well
- expected to be gone in 2020 because it's easy to test
  - vulnerability was patched with XML process in 2014
  - Zed Attack Proxy (ZAP) is a good free tool to spot this
- problem with XXE is it allows external entities
  - allows uploading of files that can then execute on a web server
  - should test for accepted files types

5. Broken Access Control

- change the URL to get someone else's data
- tools do not understand access control
  - they can detect the absence of it
  - they can't detect if it's good
- needs to be tested more often
- need to actively check access control

6. Security Misconfiguration

- used to be at number 5
- repository for all passive finding
  - detect without doing hacking
  - misconfigured header = passive finding
  - weak cyphers
- impact is not very high
- likelihood is high
- should be part of CI/CD checks

7. Cross-Site Scripting (XSS)

- moved down from number 2
- frameworks helps us with this

8. Insecure Deserialization

- chosen by the community
- impact is high but likelihood is low
- did not have a lot of data for this in the top 10
- this is about application architecture, not a tech choice
  - where are objects flowing?
  - in the old days, they stayed on the server
  - now they're going to the client and coming back
- two forms of deserialization:
  - remote command execution
    - executing a hacker's commands on a different system
  - changing the serialized objects to elevate privileges to do something interesting
    - can't trust that objects have not been tampered with
- need to put integrity for serialized objects
- need to check for object type

9. Using Components with Known Vulnerabilities

- hasn't moved positions
- need to break the build if there is a known vulnerability in dependencies
- need to make sure supply chain is clean
- CSP helps against this

10. Insufficient Loggin and Monitoring

- helps us figure out when things go wrong
- community contribution to OWASP, not backed by data b/c this is important to communicate
- high value transactions need to have an audit trail

What is gone from top 10?

- Cross-Site Request Forgery (CSRF)
  - frameworks have helped against this
  - sitting around 17 now
- Unvalidated Redirects and Forwards

Top 10 is the "minimum to avoid negligence".

- not a high standard
