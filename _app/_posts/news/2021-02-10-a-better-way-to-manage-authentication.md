---
layout: post
category: news
tags:
- open-source
title: A better way to manage authentication
date: 2021-02-10T09:47:00.000+00:00

---
big-oauth2 is an open-source\[^1\] project backed by resources from TPC Grp. UK\[^2\], a business I founded and run along with some trusted colleagues.

The aim of the project is to make OAuth2\[^3\] simple and easy to use for developers, without having to research and prototype on how to implement it. Making this as easy as possible, we aim to construct an example, express\[^4\] implementations and a simple node module to make the project as drag-and-drop as possible.

We want to stop the implementation of arbitrary, custom, insecure authentication systems- there's no need to reinvent the wheel.

This project simply allows you to communicate with services to get the same information which can be easily implemented to record into whatever you're using to manage your user data. I don't wish for developers to not learn about password hashing\[^5\] and salting\[^6\], authentications systems and platforms, practices etc but we commonly see poor implementations for authentication in production environments.

I hope to get it all finished up and start working on the express stuff by the end of March!

\[^1\]: Open-source- source code that is open and made freely available for possible modification and redistribution Wikiepedia opensource.com

\[^2\]: A company in Greater Manchester thatspretty.cool

\[^3\]: RFC 6749 - OAuth 2.0 is an authorisation framework that enables applications to obtain limited access to user accounts and information on an HTTP service OAuth information site Wikipedia IETF

\[^4\]: express- an open-source node.js web application framework commonly used when building APIs and web/mobile applications express.js site GitHub

\[^5\]: Hashing is an irreversible crypto process where a unique piece of data is generated from an input Wikipedia educative

\[^6\]: Hash/password salt helps prevent the use of rainbow tables amongst other things Crackstation