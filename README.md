A Web Page as a Place
=====================

This proposal describes the Web Presence API
to display the presence of users in a Web page.

## MOTIVATION ##

While the Web 2.0 was perceived as a move from Web documents
to Web applications, bringing instant interactions to Web pages,
and the era of Social Networks developed the feeling of belonging
to a community with instant communication tools, it is still hard
to picture a Web page as a live experience shared with the other
visitors present in the page at the same time.

This proposal aims to make it easier for users to meet other visitors
of the same Web pages and to navigate together from page to page.

## USE CASES ##

1. Café

2. Live Concert

3. Guided Tour

## PRIOR ART ##

### TogetherJS ###

* [Home Page][TogetherJS]

    > TogetherJS is a free, open source JavaScript library by Mozilla
    > that adds collaboration features and tools to your website.
    > By adding TogetherJS to your site, your users can help each other out
    > on a website in real time!

[TogetherJS]: https://togetherjs.com/

* [Technology Overview](https://togetherjs.com/docs/#technology-overview)

    > (...)
    > The core of TogetherJS is the hub:
    > this is a server that everyone in a session connects to,
    > and it echos messages to all the participants using Web Sockets.
    > (...)
    >
    > Everything that TogetherJS does is based on
    > these messages being passed between browsers.
    > It doesn't require that everyone be on the same page,
    > all it requires is that everyone in the session know
    > what hub URL to connect to (the URL is essentially the session name).
    > People can be on different sites, but the session URL is stored
    > in sessionStorage which is local to one domain
    > (and because we use sessionStorage
    > instead of localStorage,
    > it is local to one tab).
    > We don't have any techniques implemented
    > to share sessions across multiple sites,
    > but the only barrier is this local storage of session information.
    >
    > Features are built on top of this messaging system.
    > For instance when you move your mouse around,
    > a cursor-update message is sent giving the new mouse position.
    > Other clients that aren't at the same page as you
    > see the message but ignore it.

* [TogetherJS as a Postmodern Programming Tool]
  (http://www.ianbicking.org/blog/2013/10/togetherjs-a-postmodern-tool.html)

    > Our basic task/intention with TogetherJS has been
    > to enable real-time collaboration, co-browsing, co-presence.

## AUTHOR ##

Eric Bréchemier  
github@eric.brechemier.name

## LICENSE ##

CC0  
https://creativecommons.org/publicdomain/zero/1.0/
