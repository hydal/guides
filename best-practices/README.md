Best Practices
==============

A guide for programming well.

* [General](/best-practices/general)
* [Object-Oriented Design](/best-practices/object-oriented-design)
* [Node.JS](/best-practices/nodejs)
* [JavaScript](/best-practices/javascript)
* [Ruby](/best-practices/ruby)
* [Ruby Gems](/best-practices/ruby-gems)
* [Rails](/best-practices/rails)
* [Bundler](/best-practices/bundler)
* [Testing](/best-practices/testing)







Postgres
--------

* Avoid multicolumn indexes in Postgres. It [combines multiple indexes]
efficiently. Optimize later with a [compound index] if needed.
* Consider a [partial index] for queries on booleans.
* Constrain most columns as [`NOT NULL`].
* [Index foreign keys].

[`NOT NULL`]: http://www.postgresql.org/docs/9.1/static/ddl-constraints.html#AEN2444
[combines multiple indexes]: http://www.postgresql.org/docs/9.1/static/indexes-bitmap-scans.html
[compound index]: http://www.postgresql.org/docs/9.2/static/indexes-bitmap-scans.html
[partial index]: http://www.postgresql.org/docs/9.1/static/indexes-partial.html
[Index foreign keys]: https://tomafro.net/2009/08/using-indexes-in-rails-index-your-associations


Email
-----

* Use [SendGrid] or [Amazon SES] to deliver email in staging and production
environments.
* Use a tool like [MailView] to look at each created or updated mailer view
before merging.

[Amazon SES]: http://robots.thoughtbot.com/post/3105121049/delivering-email-with-amazon-ses-in-a-rails-3-app
[SendGrid]: https://devcenter.heroku.com/articles/sendgrid
[MailView]: https://github.com/37signals/mail_view




HTML
----

* Don't use a reset button for forms.
* Prefer cancel links to cancel buttons.
* Use `<button>` tags over `<a>` tags for actions.

CSS
---

* Use Sass.

Sass
----

* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
display scrollbars outside of OS X, even when content fits in the container.
* Use `image-url` and `font-url`, not `url`, so the asset pipeline will re-write
the correct paths to assets.
* Prefer mixins to `@extend`.

Browsers
--------

* Don't support clients without Javascript.
* Don't support IE6 or IE7.

