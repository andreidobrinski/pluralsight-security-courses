# What You Need To Know About HTTPS Today

[Link to course](https://app.pluralsight.com/library/courses/play-by-play-https-what-you-need-know-about-today)

HTTPS is becoming non-optional

Note about how HTTPS pages have

- the word "Secure" near the address bar
- a padlock to represent security
- http doesn't have those things

Confidentiality associated with HTTPS

- when you send data, other people won't see it
- when you load data, other people won't see it

Integrity

- knowing that nothing's been changed on the page from the original content
- eg. changing stories on a news site
- adding malware to an insecure site

Jan 2017

- Chrome and Firefox started adding a "Not secure" label when there is a password field on the page
- Chrome adds a "Not secure" tag when a user starts typing into a text box on a site without HTTPS

Authenticity

- we can trust that the person/org that created the site is the person/org that they say they are
- can't serve an invalid certificate for a domain you don't own

Browsers are deprecating features based on unsecured origins

- need HTTPS to transfer personal data
- eg geolocation

Mobile apps will need to ensure HTTPS by end of 2016

Stats

- 30% of top 1 million sites using HTTPS
- 60% of traffic is HTTPS

HTTPS is getting easier with Lets Encrypt

- free
- automated
  - easier to install and automatically renews
- has helped to grow HTTPS adoption

SSL became TLS

- SSL stays the colloquial term that people use

Cloudflare also handles HTTPS certificates

- CF's DNS serves the certificate

CF SSL Options

- Off (no https)
- Flexible - https between client and cloudflare but no https between cloudflare and the origin
  - protected against hotel wifi, protected against IPS and malicious DNS
- Full - https between CF nodes and origin site
  - need to have https on the origin
  - eg, customdomain.com doesn't have one but customdomain.azurewebsites.net has one
  - customdomain.com can point to \*.azurewebsites.net
  - \*.azurewebsites.net wont be validated against customdomain.com
  - protect against passive eavesdropping
    - connection is encrypted. anyone looking at traffic cant see it
    - doesnt protect against active interception, eg, man in the middle inserting their own certificate
- Full scrict - CF validates legitimate cert from origin website

Other benefits

- Can do Brotli compression with HTTPS
  - performance benefits
- http2 is faster than http1.1
  - http2 can only work over a TLS connection, aka with HTTPS

Certificates can only get issued to someone that proves that they control the domain that they are asking to certify

EV certificate

- shows the company name and registered country in the URL bar
- proves authentication
- more transparency than just "Secure"
- people don't expect/look for an EV cert

Mixed content

- site is served over HTTPS but has components (images etc) served over HTTP
- still at https://
- doesn't show padlock or "Secure" label
  - the page as a whole is no longer secure

Meta tag that allows only https content

- cascades down thru site's dependencies
- if it can't use https, it won't show the asset
<meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">
- works for all browsers but IE and Edge

HSTSpreload.org

- sites that can only be loaded over HTTPS
- stops the first request being over HTTP
