# Defending JavaScript Keylogger Attacks PCI

[Link to course](https://app.pluralsight.com/library/courses/defending-javascript-keylogger-attacks-pci)

Old Model

- merchants used credit card numbers in the DB as a tracking tool
  - tracking activity between online/offline shopping
- big security issue with storing credit card numbers in DB

New Model

- web server connects directly to bank/payment
- no credit card numbers stored in DB
- hackers have hacked and rewritten files on the web servers to create temp files that hold credit card info
- evolved to hackers storing the data in memory and posting it back out

Recent Model

- merchants reluctant to spend extra on PCI security
  - not their core business
  - want to focus on buying and selling products
- if merchants don't have the credit card data, they are not targets for hackers
  - they wouldnt have to spend money securing card data

Direct Post Form

- merchant has a form on their page that comes from the merchant's web server (form for credit card info)
- posts to payment provider
- merchant no longer stores, processes or transmit card holder data
- hackers would give buyers a page that said "something went wrong, please post again" while collecting the card data
  - the second time, the data would go through to the payment provider
- merchant uses a script tag from payment provider (stripe, braintree etc) to load the form
- issue: payment starts with merchant's web server and is not within scope of PCI

Recent hack

- hackers will add their script tag to the merchants site
- merchant's site loads the payment provider form, modified by hacker's JS
- hacker has control over payment form
- payment goes through, hacker sends data to themselves async

Cyber Security Framework

1. Identify

- Know how you can be attacked

2. Protect

- know how to prevent the attack

3. Detect

- know when you've been attacked

4. Respond

- know how to stop an attack

5. Recover

- know how to restore normal operations

Obfuscated Malicious JS

- script tag obfuscated with something benign, like jQuery
- malicious JS code obfuscated with regex

Checking for correct third-party JS

- adding an integrity tag with a hash
  - AKA SRI
- if JS is as expected, hash with match up
- if not, hash with not match, indicating it's been tampered with

Content security policy (CSP)

- in headers of HTTP response
- a list of where you can load different content types from
- if source isn't contained in the list, it won't run
- report-uri gives ability to send host for unexpected code when source doesn't match

[SRI Hash Generator](https://www.srihash.org)

Jscrambler

- obfuscates JS

Security must always be adapted to changes in how hackers work

Disclosure

- Must tell payment processor if/when you have a data breach
- Must tell customers, especially under GDPR or other laws (US and AUS included)
