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

TODO