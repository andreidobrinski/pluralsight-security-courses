# Payment Card Security Processing and PCI Standards

[Link to course](https://app.pluralsight.com/library/courses/payment-card-security-processing-pci-standards)

How Card Payments Work?

- Card holder goes into shop, pays by card
- Store owner wants to know that they will get paid
- Cardholder wants to know that the transaction went through and they can buy the item
- Cardholder's bank wants to know if
  - it's really the cardholder buying or if it's fraud
  - if the account has sufficient funds

First step: Authorization

- answer's the merchant and bank's question
- "if cardholder buys item will the bank give the money later?"
- bank returns the answer
- merchant sends Authorization Request
- bank sends Authorization Response (accept or decline)

Cards

- issuer name
- contactless indicator
- EMV chip (insert chip)
- Bank identifiation number (BIN)
  - first 6 digits
- Primary account number (PAN)
  - rest of card #
- cardholder name
- expiration date
- card brand
- Magnetic strip (2 tracks)
- signature strip
- hologram

Swipe method

- merchant sends tracks 1 data (Request)
- bank checks for fraud and valid funds
- bank sends a response

Four party model

- Merchant does not have a relationship with every one of it's customer's banks
- intead the merchant has a relationship with an acquirering bank that then builds relationships with every issueing bank
- Card scheme/ card brand (Visa, Mastercard etc.) connects all acquireing banks with all issueing banks

Three party model

- merchant to card brand to cardholder
  - american express and discover cards

Second step: Clearing

Four-party

- merchant sends a summary of their day's transactions to acquirer
- scheme works out which transaction is for which issueing bank
- scheme sends all transations for each bank together

Third step: Settlement

Four-party

- issueing banks sends total \$ of each transaction that the scheme asked for to the scheme
- scheme sends that \$ onto acquireing banks
- acquireing banks separate the \$ out and send it to the merchants
- the amount of time the merchant must wait for \$ varies

Exceptions

- Not all transactions are authorized
- Merchant may not send a clearing file (settlement file)
- message format differs
- sometimes there is no clearing (direct settlement from authorization)

Ecommerce

- also includes a Capture transation with authorization to confirm (by merchant) that the transaction is really happening
- could also have a Payment Service Provider
  - takes care of paperwork with banks

Fourth step: Undo - Chargeback and Refund

Merchant initiates

- merchant sends PAN, expiration date and cardholders name for return funds
- even easier for merchants with PSPs

Chargeback: undone by cardholder

- cardholder claims that either
  - the transaction was fraud or
  - the merchant didn't hold up their end of the deal
- cardholder contacts issueing bank
- issuer bank contacts acquirer bank
- merchant either agrees to chargeback or disputes it
- disputes are settled by card scheme

How Criminals Turn Stolen Card Data into Cash

- taking stolen card data and cloning the card. then using the card to take cash out of ATMs
- buying goods in shops/online and selling that for cash
- usually 4 criminals (specialties) involved

  1. stealing the data
  2. selling the data
  3. monetizing the data
  4. mule: touch the cash/goods. may not even know they're a criminal (parcel shipments)

- if a criminal steals authorization data, then they have everything they need to fake an authorization
- they can clone the data to a blank card

How a new card is made

- person asks bank for a new card
- bank has many blank cards that they ordered from a card manufacturer
- bank sends person's personalization file to the personalization bureau
- p.bureau creates the card for cardholder and ships it to them
- if a PIN in needed, they ship it a few days later

EMV Chip

- usually found in the same place
- small computer that's powered up when inserted into a device
- chip has secrets that never leave the chip, which makes it difficult for criminals to copy
- emv asks for encrypted PIN data
- payment terminal sends encrypted pin and asks if it is correct
- chip sends a cryptographic signature (cryptogram) to the terminal and pseudo mag stripe data to send to issueing bank
- terminal sends mag stripe data and cryptogram to bank
- bank validates and sends accept/decline back to terminal
  - bank generates cryptogram and checks to see if they match to validate
  - bank trusts that the crytogram can only be generated on the EMV chip
- magstripe image on chip is different from magstripe image on the stripe

Criminal's order of preference:

1. physical cards and PINs
2. physical cards
3. card data used to authorize transactions

- magstripe + PIN
- magstripe
- ecommerce data

PCI SSC - Payment Card Industry Security Standards Council

- formed to consolidate the several different standards made by different card schemes
- formed in 2006
- formed by 5 card brands (Visa, Mastercard, AmEx, JCB, Discover)
- took the best parts of these companies to make the PCI standards

5 PCI Standards

- Data Security Standard (PCI DSS)
  - protects cardholder data in organizations
- Payment Application Data Security Standard (PCI PA-DSS)
  - helps people write secure software
- PIN Transaction Standards (PCI PTS)
  - protects PINs
- Point-to-Point Encryption Standard (PCI P2PE)
  - strongly encrypts data
- Card Production

PCI DSS

- logical and physical controls
- applies to all orgs that store, process or transmit cardholder data
- 288 security requirements
- building secure networks, protect cardholder data, vulnerability mgmt program, access control, monitoring and testing, documentation

PA DSS

- software development standard
- commercial, off the shelf software
- ensures complience with PCI DSS

PTS Standards

- Point of Interaction
  - crypto key mgmt of physical payment terminals
- PIN
  - encryption and decryption
- Hardware Security Module

PIN Encryption

- it's not just the PIN that's encrypted
- the PIN combined with other data (primary acct # and operation)
- generates a 64bit PIN block
- that PIN block is then encrypted
- it becomes harder to break

P2PE

- how to encrypt Primary Account Numbers in POI device and decrypt
- key manamgement
- how to look after POI devices
- means merchant wont be able to retain cardholder data

Card production

- standards for how to manufacture, personalize and distribute payment cards
- how to send PINs to customers

PCI standards isn't generally a legal requirement

Contracts between parties

- contract between issuer and scheme
  - contract to issue cards
  - lets the issuer give cards within the scheme
  - complies with card production, PIN, DSS
- between scheme and acquirer
  - acquirer can sign up merchants and process their transactions
  - DSS and PIN
  - ensure merchants support standards DSS and POI
  - enforcement comes from acquirer
- between acquirer and merchant
  - says merchant will be able to accept all kinds of schemes

Card Schemes

- make merchants comply with PCI DSS
- make merchants' third parties comply with PCI DSS
- make acquirers comply with PCI PTS PIN
- make merchants only use PCI PA-DSS compliant software

PCI SSC

- writes standards
- train and certify assessors that validate that standards are kept
- accredits labs that test devices to comply with standard
