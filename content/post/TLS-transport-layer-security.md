---
title: "TLS Transport Layer Security"
description: "Understanding basics of TLS (transport layer security) protocol."
date: 2023-01-29T22:21:34+05:30
draft: true
aliases: ["posts", "articles", "blog", "showcase", "docs"]
author: "themayurkumbhar"
tags: ["TLS", "Transport Layer Security", "protocol", "web security"]
draft: false
---

## TLS (Transport Layer Security) ?

TLS is a security protocol aimed at enhancing privacy and protecting data during Internet communications. 
Its primary function is to encrypt communication between web servers and applications, such as when a web browser accesses a website.

> The Internet Engineering Task Force (IETF), an international standards body, proposed TLS as a means of securing internet communications. 
> TLS 1.0, the first version of the protocol, was released in 1999, and the most recent iteration, TLS 1.3, was published in 2018.

## TLS Vs. SSL?

**TLS** (Transport Layer Security) is based on the **SSL** (Secure Sockets Layer) protocol, which was developed by **Netscape**. 
**TLS 1.0** was initially intended to be **SSL 3.1**, but the name was changed before its release as it no longer had a connection to Netscape. 
Despite this, the terms TLS and SSL are often used interchangeably.

## TLS and HTTPS?

**HTTPS** is a **secure implementation** of the **TLS encryption protocol**, built on top of the **HTTP protocol**. 
It is widely used for **webservices, APIs, and websites**.

## TLS components:

1. **Encryption**: Hide data being transferred between parties, by encrypting
2. **Authentication**: Ensures that the parties exchanging information are who they claim to be.
3. **Integrity**: Verifies that the data has not been forged or tampered with.

## How TLS works?

For a website or application to implement TLS encryption, it must have a **TLS certificate** installed on its **origin server**. 
This certificate, also referred to as an "**SSL certificate**," is issued by a **certificate authority** (CA) to the domain owner. 
It contains crucial information about the **domain ownership** and the **server's public key**, 
both of which are necessary for **verifying the server's identity**.

The initiation of a TLS connection is done through a sequence known as the **TLS Handshake**. 
When a user accesses a website that utilizes TLS, the TLS Handshake process starts between the user's device, 
also known as the client device, and the web server.

**TLS handshake**:

* Specify which **version of TLS to use** (TLS 1.0, 1.2, 1.3, etc.)
* Decide on which **cipher suites to use**
* **Authenticate** the identity of the **server using the server's TLS certificate**
* **Generate session keys** for **encrypting messages** between them after the hand

The TLS Handshake establishes a cipher suite for the communication session, 
which is a set of algorithms determining the shared encryption keys or session keys to be used for that specific session.

The TLS Handshake makes sure the server is who it says it is by using public keys (Authentication). 
These public keys allow for secure data exchange and confirm the server's identity. 
The public key is found in the server's TLS certificate and is used for safe communication

Data is encrypted and verified with a message authentication code (MAC) during a TLS connection. 
The recipient checks the MAC to make sure the data is unchanged. 
This is like a seal on a bottle of medicine, showing that it hasn't been tampered with.

![three-way-handshake](../images/threeway-handshake.png "Title")

## TLS affect web application performance?

Recent TLS versions have minimal impact on web application performance. 
The setup process of a TLS connection requires time and computational resources.
The client and server communicate multiple times before data transmission, causing a delay in web application load times and using up client and server memory.

Technologies in place that help to mitigate potential latency created by the TLS handshake:

1. **TLS False Start**: Lets the server and client start transmitting data before the TLS handshake is complete.
2. **Session Resumption**: Allows clients and servers that have previously communicated to use an abbreviated handshake

It's always great to share knowledge and educate others about technical topics.
I'm glad you took the time to read my blog. If you have any questions or feedback, please feel free to reach out. 
Thanks again for reading! 😊

