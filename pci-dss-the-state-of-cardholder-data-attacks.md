# PCI DSS: The State of Cardholder Data Attacks

[Link to course](https://app.pluralsight.com/library/courses/pci-dss-state-cardholder-data-attack/table-of-contents)

PFI - PCI Forensic Investigator

- the only people allowed to do payment card investigations
- every PFI is also a QSA

How does a merchant find out they've been breached?

- customer reaches out and lets them know that they've used a card with them and the card is not being used fraudulently
- acquiring bank's algorithms will trip and let the merchant know. card brands and acquirer are monitoring transactions for fraud patterns

What should the merchant do if they find out they've been breached?

- need to notify the acquiring bank within 24hrs
- merchant calls forensic company to do investigation
- merchant and PFI can't work together on the breach if they have a pre-existing relationship

What does the PFI do?

- find out about size of network and any information about the breach
- ask for network diagrams
- how many websites are in scope of the breach
- asks the merchant to preserve the evidence
- asks the merchant to keep mission-critical infrastructure active
- keep malware preserved so it can be later investigated
- gets on site as fast as possible
- within 5 days, PFI needs to get on site and provide an initial report to card brands
- downloads image of compromised machine (HDD and RAM)
- either focuses on collecting data from machines or start premilinary forensics if there's time
- "contain" the incident; make sure the bad actors are no longer there
- does not do defense, only forensics

PFI - after the visit

- takes data back to forensic lab
- looking for evidence of when the breach first happened
- what they did to contain it
- what needs to be contained
- analyze malware, find any other back doors

Usually organized crime instead of independent bad actors.

PFI

- provide recommendation/remediation steps
- rarely goes back on site
- cases could be as little as a week and as much as six months
- confirms if PCI standards were met at the time of the incident
- notes any missing PCI steps that were relevant for the breach

Point of Sale Attacks

- huge issue in the US particularly. b/c mag stripe is still widely used
- malware runs either on individual POS or on the system as a whole
- usually through a remote access point. guest wireless network for eg - using a unsecure guest network to get an IP that can then go into the card data on the main network
- "any point that attackers can attack in theory, they are probably attacking in reality"
- ISO: vendors that serve and run the POS hardware
- remote access to POS through ISO
- multi-factor auth has helped with this. must be two-channel

Code replay attack

- attacker knows that 2fa is in place
- waits for legitimately employee to send remote access request
- sends another one directly behind them
- social engineering to have approver approve both requests

Point-to-point encryption

- PFI has yet to see a properly implemented p2pe system get breached
- still need to make sure other areas of security are in check if attacker gets on system (ransomware, crypto miners etc)

60% of work for PFI is ecommerce
80% of recent cases have been client-side attacks

- attacker have bought and certified similar-looking domains to appear authentic

File Integrity Monitoring has greatly reduced server-side attacks

OSS shopping carts

- attackers can understand their vulnerabilities
- patches must be kept up to date
- daily scanning is recommended to search for patches for shopping carts

CSP and SRI help against JS attacks
