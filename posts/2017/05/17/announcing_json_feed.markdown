@title Announcing JSON Feed
@pubDate 2017-05-17 08:02:12 -0700
@modDate 2017-05-17 08:02:12 -0700
We — Manton Reece and Brent Simmons — have noticed that JSON has become the developers’ choice for APIs, and that developers will often go out of their way to avoid XML. JSON is simpler to read and write, and it’s less prone to bugs.

So we developed JSON Feed, a format similar to [RSS](http://cyber.harvard.edu/rss/rss.html) and [Atom](https://tools.ietf.org/html/rfc4287) but in JSON. It reflects the lessons learned from our years of work reading and publishing feeds.

[See the spec](https://jsonfeed.org/version/1). It’s at version 1, which may be the only version ever needed. If future versions are needed, version 1 feeds will still be valid feeds.

#### Notes

We have a [WordPress plugin](https://github.com/manton/jsonfeed-wp) and, in the future, a JSON Feed Parser for Swift. Unofficial Swift parsers, and JSON Feed tools for other languages and platforms, are available on [the code page](https://jsonfeed.org/code).

See [Mapping RSS and Atom to JSON Feed](https://jsonfeed.org/mappingrssandatom) for more on the similarities between the formats.

This website — the Markdown files and supporting resources — [is up on GitHub](https://github.com/brentsimmons/JSONFeed), and you’re welcome to comment there.

This website is also a blog, and you can subscribe to the [RSS feed](https://jsonfeed.org/xml/rss.xml) or the [JSON feed](https://jsonfeed.org/feed.json) (if your reader supports it).

We worked with a number of people on this over the course of several months. We list them, and thank them, at the bottom of the [spec](https://jsonfeed.org/version/1). But — most importantly — [Craig Hockenberry](http://furbo.org/) spent a little time making it look pretty. :)
