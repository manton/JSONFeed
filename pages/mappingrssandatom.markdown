@title Mapping RSS and Atom to JSON Feed
# Mapping RSS and Atom to JSON Feed

Though [RSS](http://cyber.harvard.edu/rss/rss.html) and [Atom](https://tools.ietf.org/html/rfc4287) are XML and [JSON Feed](https://jsonfeed.org/version/1) isn’t, there are a number of similarities. Here’s how to map them.

## RSS

### Channel

While RSS has a `channel` top-level element, JSON Feed puts the corresponding information at the top level.

* RSS `title` and `description` map directly to JSON. An RSS `link` maps to `home_page_url`.

* `cloud` element is similar in purpose to the JSON Feed `hubs` item.

* RSS has `webmaster` and `managingEditor` items, while JSON Feed has an `author` item.

* `image` is superficially like a JSON Feed `icon` — except that the JSON Feed version should be square, and the RSS image should be wider than it is tall. These map only in the case that your RSS image is already square.

### Item

RSS has an array of `item` objects, and so does JSON Feed.

* `title` maps directly, with the caveat that it must be plain text in JSON Feed. (Note: `title` is optional in both RSS and JSON Feed.)

* `link` maps to `url` and to `external_url`. The `url` must be a permalink, a link to the content of the item. When an item links to another page — as in a linkblog — then `external_url` must be the URL of that other page. (See the [Daring Fireball JSON feed](https://daringfireball.net/feeds/json) for an example.)

* `description` maps to `content_html` and to `content_text`. Choose the one that fits. A Twitter-like service might use `context_text`, while a blog might use `content_html`.

* `guid` maps to `id`. In RSS, `guid` can have an `isPermaLink` attribute; in JSON Feed the `url` must be the permalink, and `id` *may* be the same as `url`, though it doesn’t have to be.

* The `author` element is a single value, while in JSON Feed it’s an object with `name`, `url`, and `avatar` values.

* `pubDate` maps to `date_published`, but this date and others in JSON Feed use a different format, the ISO 8601 format. (Example: `2010-02-07T14:04:00-05:00`.)

* `enclosure` maps to `attachments` — but JSON Feed allows for multiple attachments. An RSS `enclosure` has attributes `url`, `length`, and `type`, and the JSON Feed attachment object has corresponding elements `url`, `size_in_bytes`, and `mime_type`. JSON Feed adds `title` and `duration_in_seconds`.

* `category` maps to `tags`. In RSS a `category` can have a `domain` attribute, and there’s no equivalent in JSON Feed.

## Atom

### Feed

Unlike RSS's `channel` element, Atom puts many of the elements to describe a feed at the top level of the document, just like JSON Feed.

* Atom's `title` maps directly to JSON Feed.
* Atom uses `link` elements to show the relationship between the feed and other URLs. Without a `rel` attribute, or with `rel="alternate"`, Atom's `link` is equivalent to JSON Feed's `home_page_url`. With `rel="self"`, it maps to JSON Feed's `feed_url`.
* Atom has `subtitle` and `id` elements. There is no mapping for these in JSON Feed, although `description` in JSON could be used instead of `subtitle`.

### Entry

Atom has an array of `entry` objects. In JSON Feed these are `item` objects.

* Atom's `title`, `id`, and `summary` map directly to JSON. In JSON, however, `title` and `summary` are always plain text.
* Atom uses a content's `type` attribute to declare whether the text is plain text or HTML. `type="html"` or `type="xhtml"` in an Atom feed maps to `content_html` in JSON. `type="text"` maps to `content_text` in JSON.
* `link` with `rel="alternate"` maps to `url` in JSON. If `rel="related"` is used for links to an external site, in JSON Feed those map to `external_url`.
* The `author` element contains `name`, `uri`, and `email`, while in JSON Feed it's an object with `name`, `url`, and `avatar` values.
* Atom's `published` and `updated` dates map to `date_published` and `date_modified` in JSON. Both Atom and JSON Feed use the same date format.
* Atom's `link` with `rel="enclosure"` maps to `attachments` in JSON Feed. An Atom enclosure has attributes `href`, `length`, and `type`, and the JSON Feed attachment object has corresponding elements `url`, `size_in_bytes`, and `mime_type`. JSON Feed adds `title` and `duration_in_seconds`.