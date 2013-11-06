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
    > **hCard**
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
    > **Data Formats**
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

### Extensible Messaging and Presence Protocol (XMPP) ###

* [XMPP Standards Foundation](http://xmpp.org/)

    > The Extensible Messaging and Presence Protocol (XMPP)
    > is an open technology for real-time communication,
    > which powers a wide range of applications
    > including instant messaging, presence, multi-party chat,
    > voice and video calls, collaboration, lightweight middleware,
    > content syndication, and generalized routing of XML data.
    > (...)

* [RFC 3921 - XMPP: Instant Messaging and Presence]
  (http://www.ietf.org/rfc/rfc3921.txt)

    > § 5. Exchanging Presence Information
    >
    > Exchanging presence information is made relatively straightforward
    > within XMPP by using presence stanzas.  However, we see here a
    > contrast to the handling of messages: although a client MAY send
    > directed presence information to another entity by including a 'to'
    > address, normally presence notifications (i.e., presence stanzas with
    > no 'type' or of type "unavailable" and with no 'to' address) are sent
    > from a client to its server and then broadcasted by the server to any
    > entities that are subscribed to the presence of the sending entity
    > (in the terminology of RFC 2778 [IMP-MODEL], these entities are
    > subscribers).
    > (...)
    >
    > § 6. Managing Subscriptions
    >
    > In order to protect the privacy of instant messaging users and any
    > other entities, presence and availability information is disclosed
    > only to other entities that the user has approved.  When a user has
    > agreed that another entity may view its presence, the entity is said
    > to have a subscription to the user's presence information.  A
    > subscription lasts across sessions; indeed, it lasts until the
    > subscriber unsubscribes or the subscribee cancels the
    > previously-granted subscription.  Subscriptions are managed within
    > XMPP by sending presence stanzas containing specially-defined
    > attributes.
    > (...)

## RELATED WORK ##

### vCard ###

* [RFC 2426 - vCard MIME Directory Profile]
  (https://tools.ietf.org/html/rfc2426)

    > This memo defines the profile of the MIME Content-Type [MIME-DIR] for
    > directory information for a white-pages person object, based on a
    > vCard electronic business card. The profile definition is independent
    > of any particular directory service or protocol. The profile is
    > defined for representing and exchanging a variety of information
    > about an individual (e.g., formatted and structured name and delivery
    > addresses, email address, multiple telephone numbers, photograph,
    > logo, audio clips, etc.).
    > (...)

### hCard ###

* [hCard 1.0](http://microformats.org/wiki/hcard)

    > hCard is a simple, open format for publishing
    > people, companies, organizations on the web,
    > using a 1:1 representation of vCard (RFC2426)
    > properties and values in HTML.
    > hCard is one of several open microformat standards
    > suitable for embedding data in HTML/HTML5,
    > and Atom/RSS/XHTML or other XML.

### Page Visibility ###

* [W3C Recommendation](http://www.w3.org/TR/page-visibility/)

    > (...)
    > The Page Visibility specification defines a means
    > for site developers to programmatically determine
    > the current visibility of a document
    > and be notified of visibility changes.
    > Without knowing the visibility state of a page,
    > web developers have been designing webpages
    > as if they are always visible.
    > This not only results in higher machine resource utilization,
    > but it prevents web developers from making runtime decisions
    > based on whether the webpage is visible to the user.
    > Designing web pages with knowledge of the page visibility
    > will allow for improved user experiences and power efficient sites.
    >
    > With this interface, web applications may chose to alter behavior
    > based on whether they are visible to the user or not.
    > For example, this interface can be used to scale back work
    > when the page is no longer visible.
    > If a web based email client is visible,
    > it may check the server for new messages every few seconds.
    > When hidden it might scale checking email to every few minutes.
    > This interface can also be used to provide better runtime
    > user experience decisions not related to power management.
    > For example, a puzzle game could be paused
    > when the user no longer has the game visible.
    > Further, this interface can be used by advertisers
    > to not charge for ads that are not visible to users.
    > (...)

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

### Device APIs Requirements ###

* [W3C Working Group Note](http://www.w3.org/TR/dap-api-reqs/)

    > §8 Contacts
    >
    >  This interface:
    >
    > * MUST enable listing all available address books on the device;
    > * MUST enable listing all contacts in the address book(s);
    > * MUST enable reading the details for a contact;
    > * SHOULD enable creating a new contact;
    > * SHOULD enable updating a contact;
    > * SHOULD enable deleting a contact;
    > * SHOULD enable filtering the list of contacts to search for a subset.

### WebRTC: Real-Time Communication between browsers ###

* [Home Page](http://www.webrtc.org/)

    > WebRTC is a free, open project that enables web browsers
    > with Real-Time Communications (RTC) capabilities
    > via simple Javascript APIs.
    > The WebRTC components have been optimized to best serve this purpose.
    >
    > Our mission: To enable rich, high quality, RTC applications
    > to be developed in the browser via simple Javascript APIs and HTML5.
    >
    > The WebRTC initiative is a project supported by Google, Mozilla
    > and Opera. This page is maintained by the Google Chrome team.

* [WebRTC Protocol at IETF]
  (https://datatracker.ietf.org/wg/rtcweb/)

* [WebRTC API at W3C]
  (http://dev.w3.org/2011/webrtc/editor/webrtc.html)

### Geolocation API Specification ###

* [W3C Recommendation](http://www.w3.org/TR/geolocation-API/)

    > The Geolocation API defines a high-level interface
    > to location information associated only with the device
    > hosting the implementation, such as latitude and longitude.
    > The API itself is agnostic of the underlying
    > location information sources.
    > (...)
    >
    > User agents must not send location information to Web sites
    > without the express permission of the user.
    > User agents must acquire permission through a user interface,
    > unless they have prearranged trust relationships with users (...)
    >
    > Recipients must only request location information when necessary.
    > Recipients must only use the location information for the task
    > for which it was provided to them.
    > Recipients must dispose of location information
    > once that task is completed,
    > unless expressly permitted to retain it by the user.
    > Recipients must also take measures
    > to protect this information against unauthorized access.
    > If location information is stored,
    > users should be allowed to update and delete this information.
    >
    > The recipient of location information must not retransmit
    > the location information without the user’s express permission.
    > Care should be taken when retransmitting
    > and use of encryption is encouraged.
    >
    > Recipients must clearly and conspicuously disclose the fact
    > that they are collecting location data,
    > the purpose for the collection,
    > how long the data is retained,
    > how the data is secured,
    > how the data is shared if it is shared,
    > how users may access, update and delete the data,
    > and any other choices that users have with respect to the data.
    > (...)

## REFERENCES ##

* [Presence information (Wikipedia)]
  (https://en.wikipedia.org/wiki/Presence\_information)

* [Web Application Privacy Best Practices]
  (http://www.w3.org/TR/app-privacy-bp/)

* [The Platform for Privacy Preferences 1.0 (P3P1.0) Specification]
  (http://www.w3.org/TR/P3P/)

## AUTHOR ##

Eric Bréchemier  
github@eric.brechemier.name

## LICENSE ##

CC0  
https://creativecommons.org/publicdomain/zero/1.0/
