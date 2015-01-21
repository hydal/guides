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
* [Postgres](/best-practices/postgres)






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

