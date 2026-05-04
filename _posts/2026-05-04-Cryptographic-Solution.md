---
title: "1.4 Crpytographic Solutions"
date: 2026-05-04 17:36:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/encryption.svg
  alt: Encryption
---

# 1.4.1 Public Key Infrastructure
As I have learned from coursework, **PKC is more scalable than symmetric encryption**.
PKC is basically having public and private key, public key is published and then message can be
encrypted using the public key and decrypted by private key. Can also be the reverse (public to decrypt).

It is **computationally hard to retrieve private key from public key** as they rely on the hardness of
mathematical problems like factorisation. (meaning it might be vulnerable to quantum)

### Certificate Authority
It is how certificates are signed and how trust is being chained together. Users will have root CAs,
CAs that is hardcoded onto the device and another CA's certificate being signed by root CA will mean
the CA is now rusted. When you trust a CA, you will trust any certificates that it has signed.

This is how VPN concentrators actually work, they verify company laptops using the CA-signed certificate.

### Key Escrow
A way to manage a large number of keys (from many users), allowing you to access encrypted data even if
original key holder is now gone. A legitimate business arrangment for employees leaving, shares project
data with governemnt.

The private keys are stored with **trusted 3rd party or internally**, adds availability.

---

# 1.4.2 Encrypting Data
We will explore more about the various use cases of encryption since these are not covered in class.

For data at rest (stored data), we can have full disk encryption (entire storage device) and file-level 
encryptions (individual files or folders).

For database, we can choose:
1. Transparent encryption - entire database
2. Column-Level encryption - sensitive columns (personal id)
3. Record-level encryption - individual records

Encrypting only where it matters make searches easier with less overhead!

For data in transit, we have HTTPS/TLS, VPNs use SSL/TLS and site to site VPN is IPsec.

## Encryption Algorithms
Both sides need to make use of the same algo to work. The algo is public and only the key is kept secret.

#### Key Length and Brute force
We can make use of brute force to find the key but by extending it, it gets exponentially harder to compute.

###### Key Stretching/Strengthening
Applying encryption or hashing function multiple times make brute force harder

---

# 1.4.3 Key Exchange
Out-of-band key exchange: exchaging keys without the internet!
In-band key exchange, on the network, using PKC to set up symmetric key

## In-Band Key Exchange

#### The First Way: PKC to deliver symmetric key
Client encrypts symmetric with server public key, server decrypts with private key to set up session key.

> Session keys should be changed often (ephemeral keys) and random
{: .prompt-warning}

#### The Second Way: forming symmetric key with asymmetric key
DHKE that we have learned using RSA is an example.

---

# 1.4.4 Encryption Technologies
Modern systems also make use of hardware to handle cryptographic functions more securely and efficeintly.

### Trusted Platform Module (TPM)
A standardised chip on motherboard dedicated for crypto functions on that device.

| Function | Detail |
|----------|--------|
| **Random number / key generation** | Hardware-based randomness — more secure than software |
| **Persistent memory** | Keys burned into the TPM are unique to that machine |
| **Secure key storage** | Stores keys locally, e.g. BitLocker encryption keys |
| **Brute-force resistant** | Password protected; no dictionary or brute-force attacks possible against TPM-stored data |


### Hardware Security Module (HSM)
A enterprise-grade hardware for a lot of devices

| Function | Detail |
| --- | --- |
| **Centralised key storage** | Stores encryption keys for all servers in a data centre |
| **Cryptographic acceleration** | Dedicated hardware performs encrypt/decrypt in real time |
| **Redundancy** | Clustered with redundant power and network — always available |
| **Authorised access only** | Prevents unauthorised access to stored keys |

can connect to plug-in card or another hardware with faster encryption

### Key Management System
With TPMs, HSMs, user certificates, all other keys and certificates all in use at the same time,
you will need a centralised system to manage everything.

| Feature | Detail |
| --- | --- |
| **Centralised console** | Manage all key types from one interface |
| **On-premises or cloud** | Flexible deployment |
| **Key separation** | Keys stored separately from the data they protect |
| **Automatic key rotation** | Regularly cycles keys without manual intervention |
| **User association** | Assign specific keys to specific users |
| **Logging and reporting** | Full audit trail of key usage, active/inactive keys |

### Secure Enclave
A dedicated privacy processor built directly into consumer devices (phone, tablet, laptop)
separate from the CPU.

some of its features include:

| Capability | Detail |
| --- | --- |
| **Separate processor** | Not the main CPU — dedicated solely to privacy/security |
| **Own boot ROM** | Boots independently; monitors system processes during main boot |
| **True random number generator** | Hardware-based randomness for cryptographic operations |
| **Real-time memory encryption** | Encrypts/decrypts data as it moves in and out of memory |
| **Built-in cryptographic keys** | Hardcoded root keys that cannot be changed — root of trust |
| **AES encryption in hardware** | Performs AES without involving the main CPU |
| **Process monitoring** | Monitors all processes on the system, especially at boot |

---

# 1.4.5 Obfuscation
The meaning of obfuscation is to make data harder to understand without having to encrypy it.
It is **security through obscurity**, not really truly secure on its own!

## Steganography
hiding data inside another file or medium. The file containing the hidden data is known as **covertext**.
Recovery will require you knowing the tool/method used to hide it.

There are multiple types of steganography: Image, Audio, Video, Network traffic, printed documents

#### Machine Identification Codes (printer dots)
This is a form of staganography built into hardware. It is difficult to see but the dots encode information
that identifies the specific printer used.

## Tokenisation
Replacing sensitive data with non sensitive subsitute (token) that has no mathematical relationship to the original.

![Alt text](/assets/images/tokenisation.jpg)
This image is a screenshot from Professor Messer's Youtube Video on Obfuscation.

Tokenisation is powerful as no encryption is required and the attacker cannot reverse engineer the
original number from the token. It is one time use, even if it is intercepted, a used token is worthles.

## Data Masking
Hiding parts of sensitive data and showing only a portion. For example, showing only last 4 digits of credit card
number.

> Data masking is different from Tokenisation as it reveals a part of the original while tokenisation completely
> replaces it with an unrelated value
{: .prompt-warning}

---

# 1.4.6 Hashing and Digital Signatures
## Hash
Quick Review: Takes an arbitrary size input and output fixed digest. Collision Resistant, Pre-Image Resistant.

MD5 no longer secure.

### Use Case 1: File Integrity Verfication
Hash posten alongside with file, once downloaded, hash the file and check if they match

### Use Case 2: Password Storage
Store hashed password instead of actual password, hashed input is compared with stored hash.

#### Problem: Rainbow Tables
A rainbow table is a pre-compiled lookup of every possible input and its hash. Attackers uses this table to
retrieve original password quickly. This can be solved with **salted hashes**.

A **salt** is a random data added to each password before hashing, every user will get a different random salt.
Every user will have different reandom salt.

### Use Case 3: Digital Signatures
Combines hashing and asymmetric encryption to provide integrity and origin (previously covered).

## Key thing to note:
Hashing is a one way process while Encryption is both ways. Hash is meant mainly for integrity and
password storage. **Keys are not required**.

---

# 1.4.7 Blockchain Technology
A distributed ledger where everyone maintains it, no single part controls it and hashing makes any
tampering immediate detectable. 

| Property | What it means |
| --- | --- |
| **Distributed** | Every participant maintains a full copy of the ledger |
| **Transparent** | Anyone participating can see the ledger |
| **Decentralised** | No single authority controls it |
| **Tamper-evident** | Any modification to a past record is immediately detectable |

How blockchain works with transactions:
1. Transaction occurs
2. Transaction details broadcasted to all participants in blockchain
3. Participants' devices store the transaction
4. Trnasactions are grouped into a block
5. A hash is added to the block (the block is a snapshot of recent transactions)
6. Completed block distributed to every copy of the ledger
7. If anyone modifies a past transaction, block's hash will not match
8. block rejected

Each block contains a hash of all transactions, any changes will cause the hash to change.

---

# 1.4.8 Certificates
Standard format: X.509
Content:

| Field | What it contains |
| --- | --- |
| **Serial number** | Unique identifier for the certificate |
| **Version** | X.509 version |
| **Signature algorithm** | Algorithm used to sign the certificate |
| **Issuer** | The CA that signed the certificate |
| **Subject** | The entity the certificate belongs to |
| **Public key** | The certificate holder's public key |
| **Subject Alternative Name** | Additional domain names covered (wildcard support) |
| **CRL Distribution Points** | Where to find the revocation list |

Certificates are based on trust, and we look at CAs to decide if we trust the website.

## Root of Trust
The trust starts somewhere and it anchors the entire chain. They might be:
- Hardware (HSM, Secure Enclave)
- Software
- Firmware
- CA

Browsers have a built-in list of trusted root CAs. Root CAs sign intermediate CAs and 
intermediate CAs sign end-entity certificates.

![Alt text](/assets/images/CSR_process.jpg)
A screenshot from Professor Messer's Youtube Video on Certificate 

## Internal CAs
Since we need to pay for CAs to validate ourselves, we can save money if we have Internal
CAs controlled within the organisation. We just need to install the CA software locally
and distribute the internal CA's public certificate to all devices in the organisation
and now all devices will trust the internal CA.

## Wildcard Certificates
Subject Alternative Name (SAN) field lists all domains that the cert covers. So not just
a single webpagebut all subdomains covered by the domain with the *.

## Certificate Revocation
Certificates have to be revoked at some point:
1. server compromised
2. private key compromised
3. cert expires
4. vulnerability discovered

There are multiple ways to do it:

#### Certificate Revocation List
It is a list of all revoked certificates maintained on CA.

Brower connects to website, receives cert and find CRL from cert. It will download the CRL
and verify if the cert is on it, if found, reject.

The disadvantage is that the CRL file is large and downloading will take a long time

#### Online Certificate Status Protocol (OCSP)
Checks the certificate status rather than downloading a full list. The browser will send the 
cert serial number to the OCSP server and will get back a status.

#### OCSP Stapling
Web server itself fetches OCSP status from CA and embed it in the TLS hanshake. Since the
status is signed by CA, web server cannot lie. No need for a separate trip to OCSP server.

| Method | How it works | Efficiency |
| --- | --- | --- |
| **CRL** | Download full revocation list | Slowest |
| **OCSP** | Query status of one cert from CA's OCSP server | Better |
| **OCSP Stapling** | Status embedded in TLS handshake by the server | Fastest |

---

# Summary
This chapter was very long, I consolidated everthing together. A lot of topics were previously 
covered and its more of refreshing my memory. Also, starting to pick up the pace!

Time to gather energy from food pictures..

![Alt text](/assets/images/kimchi_pork.jpeg)