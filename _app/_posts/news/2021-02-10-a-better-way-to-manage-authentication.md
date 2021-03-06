---
layout: post
category: news
tags:
- open-source
title: A better way to manage authentication
date: 2021-02-10T09:47:00.000+00:00

---
[big-oauth2](https://github.com/tpcofficial/big-oauth2) is an open-source[^1] project backed by resources from TPC Grp. UK[^2], a business I founded and run along with some trusted colleagues.

The aim of the project is to make OAuth2[^3] simple and easy to use for developers, without having to research and prototype on how to implement it.
Making this as easy as possible, we aim to construct an example, express[^4] implementations and a simple node module to make the project as drag-and-drop as possible.

We want to stop the implementation of arbritriary, custom, insecure authentication systems- [there's no need to reinvent the wheel](https://securitytoday.com/Articles/2019/08/01/Dont-Reinvent-the-Wheel.aspx).

This project simply allows you to communicate with serivces to get the same information which can be easily implemented to record into whatever you're using to manage your user data. I don't wish for developers to not learn about password hashing[^5] and salting[^6], authentications systems and platforms, practices etc but we commonly see poor implementations for authentication in production environments.

Me and a few friends and colleagues will be working on the open-source project in our spare time, but I quite a lot going on balancing uni crap, college, work, personal projects (what I guess this is one of) and my college projects (of which I have 3).

I hope to get it all finished up and start working on the express stuff by the end of March!

[^1]: Open-source- source code that is open and made freely available for possible modification and redistribution [Wikiepedia](https://en.wikipedia.org/wiki/Open_source) [opensource.com](https://opensource.com/resources/what-open-source)

[^2]: A company in Greater Manchester [thatspretty.cool](https://thatspretty.cool)

[^3]: RFC [6749](https://tools.ietf.org/html/rfc6749) - OAuth 2.0 is an authorisation framework that enables applications to obtain limited access to user accounts and information on an HTTP service [OAuth information site](https://oauth.net/2/) [Wikipedia](https://en.wikipedia.org/?title=OAuth2&redirect=no) [IETF](https://tools.ietf.org/html/rfc6749)

[^4]: express- an open-source node.js web application framework commonly used when building APIs and web/mobile applications [express.js site](https://expressjs.com/) [GitHub](https://github.com/expressjs/express)

[^5]: Hashing is an irreversible crypto process where a unique piece of data is generated from an input [Wikipedia](https://securitytoday.com/Articles/2019/08/01/Dont-Reinvent-the-Wheel.aspx) [educative](https://www.educative.io/edpresso/what-is-hashing)

[^6]: Hash/password salt helps prevent the use of [rainbow tables](https://en.wikipedia.org/wiki/Rainbow_table) amongst other things [Crackstation](https://crackstation.net/hashing-security.htm)