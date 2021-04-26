---
layout: post
title:  "Public Key Infrastructure (PKI)"
description: "public key infrastructure"
date:   2021-04-26 08:20:11 +0300
categories: jekyll update
---

# What is Public Key Infrastructure? A brief overview.
According to wikipedia, a public-key infrastructure (PKI) is a set of roles, policies, hardware, software and procedures needed to create, manage, distribute, use, store and revoke digital certificates and manage public-key encryption.

The purpose of a PKI is to facilitate the secure electronic transfer of information for a range of network activities such as e-commerce, internet banking and confidential email. It is required for activities where simple passwords are an inadequate authentication method and more rigorous proof is required to confirm the identity of the parties involved in the communication and to validate the information being transferred.

In cryptography, a PKI is an arrangement that binds public keys with respective identities of entities (like people and organizations). The binding is established through a process of registration and issuance of certificates at and by a certificate authority (CA). Depending on the assurance level of the binding, this may be carried out by an automated process or under human supervision. When done over a network, this requires using a secure certificate enrollment or certificate management protocol such as CMP.

Common examples of PKI today are SSL/TLS certificates on websites so that site visitors know they’re sending information to the intended recipient, digital signatures, and authentication for Internet of Things devices.

## Introducing Certificate Authorities
A certificate authority, also known as a certification authority, is a trusted organization that verifies websites (and other entities) so that you know who you’re communicating with online. Their objective is to make the internet a more secure place for organizations and users alike. This means that they play a pivotal role in digital security.

### How does a Certification Authority work?
We can simply say that a Certificate Authority is like a passport Authority in real life. They issue passports to people that they can use to actually prove who they claim to be. Similarly, a Certificate Authority issues a certificate to a website to prove its legitimacy to users. Some of the tasks performed by the CA include;
* Vet domain names, individuals and organizations to validate their identities through official records.
* Issue digital certificates that authenticate servers, individuals and organizations (establishing trust).
* Maintain certificate revocation lists that indicate when certificates become invalid prior to their expiry dates.

## The process of Verfication
It starts when a website tries to obtain a digital certificate. The certificate authority completes a verification process, depending on the type of certificate requested:
* **Domain validation** — The certificate authority verifies that the requestor is the legitimate manager of the domain/website. This means that domain validation is the minimum in terms of validation.
* **Organization validation** — The certificate authority goes a step further and performs basic business validation. This process involves a human element. Basically, the CA reviews information that the certificate requestor provides and also researches additional information (using third-party records and sources) to ensure the organization is legitimate.
* **Extended validation** — This is the most thorough level of business validation. In this one- to five-day validation process, the CA takes an extensive look at the requestor’s organization. They go above and beyond the requirements of the organization validation process to ensure that your organization truly is legitimate. 

![how-a-CA-works](/assets/images/CA.png)

## Public Keys and Private Keys
Public keys and private keys help to ensure the security of exchanges data between a client and a server.

Public keys enable;
* Users to encrypt a message to other individuals on the system
* You can confirm a signature signed by someone’s private key

Private keys enable;
* You can decrypt a message secured by your public key
* You can sign your message with your private key so that the recipients know the message could only have come from you.

### How do private and public keys ensure security of messages and identity of the sender
When looking to ensure security of messages, the sender looks up the recipient's public key and uses it to encrypt the message. The message can be transmitted openly over the Internet, and since only the recipient can decrypt the message with the appropriate private key, secure transmission is ensured.

But the order of using the key pairs can flip to ensure the identity of the sender. If a sender uses a private key to encrypt a message, the recipient can use the sender's public key to decrypt and read it. Since anyone can decrypt the message with the sender's public key, the message transmission is not necessarily secure, but since the private key is known only to the sender, the message is guaranteed to have come from that machine.

![public-and-private-key](/assets/images/private-public-key.jpg)