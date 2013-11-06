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

### Gravatar ###

* [Home Page][Gravatar]

    > Your Gravatar is an image
    > that follows you from site to site
    > appearing beside your name
    > when you do things like comment or post on a blog.
    > (...)

[Gravatar]: https://secure.gravatar.com/

* [Developer Resources](https://secure.gravatar.com/site/implement/)

    > Gravatar 'APIs' require no authentication,
    > and are all based around simple HTTP GET requests.
    > (...)

* [Image Requests](https://secure.gravatar.com/site/implement/images/)

    > Gravatar images may be requested just like a normal image,
    > using an IMG tag.
    > To get an image specific to a user,
    > you must first calculate their email hash.
    >
    > The most basic image request URL looks like this:
    >
    >     http://www.gravatar.com/avatar/HASH
    >
    > (...)
    >
    > By default, images are presented at 80px by 80px
    > if no size parameter is supplied.
    > You may request a specific image size,
    > which will be dynamically delivered from Gravatar
    > by using the s= or size= parameter
    > and passing a single pixel dimension
    > (since the images are square):
    >
    >     http://www.gravatar.com/avatar/205e460b479e2e5b48aec07710c08d50?s=200

* [Profile Requests](https://secure.gravatar.com/site/implement/profiles/)

    > Users may optionally enter a variety of profile information
    > to associate with their Gravatar account.
    > This information is openly-accessible
    > using a similar process to requesting images.
    >
    > A simple profile link looks like this:
    >
    >     http://www.gravatar.com/HASH
    >
    > (...)
    >
    > An important point to note is that
    > profile requests will only resolve for the hash
    > of the primary address on an account.
    > Users may have multiple addresses on a single account,
    > so while a Gravatar image request may return a result,
    > a profile request for the same hash may not.
    >
    > *hCard*
    >
    > Profile pages are fully marked up using hCard,
    > a microformat for programmatically embedding information
    > about people, companies, organizations, and places
    > in HTML and other markup languages. (...)
    >
    > 1. *Email address* marked up with `class=email`
    >    (only available via JS/client-side parsing
    >    due to spam-protection measures)
    >
    > 2. *IM accounts* marked up using `class=url`
    >    (some values only available via JS/client-side parsing
    >    due to spam-protection measures)
    >
    > 3. *Phone numbers* marked up with `class=tel`
    >    (using type/value subproperties)
    >
    > 4. *Verified accounts* marked up with `class=url` and `rel=me`
    >
    > 5. *Name* marked up with `class=fn`
    >
    > 6. *Personal Links* are marked up with `class=url`
    >
    > 7. *Image* (main Gravatar) is marked up using `class=photo`
    >
    > *Data Formats*
    >
    > Profile data may be requested in different data formats
    > for simpler programmatic access.
    > The following formats are supported:
    >
    > 1. JSON
    > 2. XML
    > 3. PHP
    > 4. VCF/vCard
    > 5. QR Code

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

### Firefly ###

* [Home Page][Firefly]

    > Browser-sharing is what Firefly does.
    > With browser-sharing, a customer that needs help
    > only shares the specific webpage that they are on.
    > They don't share their entire computer.
    > Browser-sharing is also typically done from one person to another,
    > and not from one person to an entire group.
    > Browser-sharing is more privacy focused than traditional screensharing.
    > Our implementation also requires no downloads for the customer,
    > and works completely in the browser with JavaScript.

[Firefly]: http://usefirefly.com/

## RELATED WORK ##

### Mozilla Labs Social API ###

* [Wiki](https://wiki.mozilla.org/Labs/SocialAPI)

    > §1.9 Interactions with Content
    >
    > With the user's understanding and consent,
    > the browser can take a more active role
    > in the interactions between content and social systems.
    > It could, for example, notice the presence of markup in the page
    > requesting a "social browsing" experience.
    > If the user has activated a social browsing feature,
    > the browser could send a signal
    > to one or more of the user's active platform providers,
    > with a "the user is currently looking at..." message,
    > at a user-specified level of granularity
    > (whole-site, or individual URL).
    > The social provider could use this
    > to provide specific content recommendations in a sidebar,
    > or to suggest immediate social interactions.
    >
    > This could, for example, be used with a HTML5 game application.
    > When the user loads the site, the browser could send a signal
    > to the social provider, which immediately could display a list
    > of which of the user's friends are currently playing -
    > or would be interested in playing a turn-based game,
    > if they're not online right now.
    >
    > Site developers could also benefit from awareness
    > that the user's browser has already provided social browsing behavior,
    > allowing them to stop using valuable page space
    > for behavior that is duplicated by the browser.
    > A set of JavaScript APIs, for example, could indicate to a site
    > that the user is already browsing socially
    > and has share functionality built into the browser,
    > so the site should focus on its displaying content.
    > Getting this interaction right will require careful attention
    > to the privacy and security characteristics of these APIs,
    > as well as the interactions and visual design of the sidebar.

* [GitHub Project](https://github.com/mozilla/socialapi-dev)

## AUTHOR ##

Eric Bréchemier  
github@eric.brechemier.name

## LICENSE ##

CC0  
https://creativecommons.org/publicdomain/zero/1.0/
