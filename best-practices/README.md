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



Testing
-------

* Avoid `any_instance` in rspec-mocks and mocha. Prefer [dependency injection].
* Avoid `its`, `let`, `let!`, `specify`, and `before` in RSpec.
* Avoid using `subject` explicitly *inside of an* RSpec `it` block.
[Example][subject-example].
* Avoid using instance variables in tests.
* Disable real HTTP requests to external services with
`WebMock.disable_net_connect!`.
* Don't test private methods.
* Test background jobs with a [`Delayed::Job` matcher].
* Use [stubs and spies] \(not mocks\) in isolated tests.
* Use a single level of abstraction within scenarios.
* Use an `it` example or test method for each execution path through the method.
* Use [assertions about state] for incoming messages.
* Use stubs and spies to assert you sent outgoing messages.
* Use a [Fake] to stub requests to external services.
* Use integration tests to execute the entire app.
* Use non-[SUT] methods in expectations when possible.

[dependency injection]: http://en.wikipedia.org/wiki/Dependency_injection
[explicit subject example]: /style/samples/testing.rb#17
[`Delayed::Job` matcher]: https://gist.github.com/3186463
[stubs and spies]: http://robots.thoughtbot.com/post/159805295/spy-vs-spy
[assertions about state]: https://speakerdeck.com/skmetz/magic-tricks-of-testing-railsconf?slide=51
[Fake]: http://robots.thoughtbot.com/post/219216005/fake-it
[SUT]: http://xunitpatterns.com/SUT.html



Bundler
-------

* Specify the [Ruby version] to be used on the project in the `Gemfile`.
* Use a [pessimistic version] in the `Gemfile` for gems that follow semantic
versioning, such as `rspec`, `factory_girl`, and `capybara`.
* Use a [versionless] `Gemfile` declarations for gems that are safe to update
often, such as pg, thin, and debugger.
* Use an [exact version] in the `Gemfile` for fragile gems, such as Rails.

[Ruby version]: http://bundler.io/v1.3/gemfile_ruby.html
[exact version]: http://robots.thoughtbot.com/post/35717411108/a-healthy-bundle
[pessimistic version]: http://robots.thoughtbot.com/post/35717411108/a-healthy-bundle
[versionless]: http://robots.thoughtbot.com/post/35717411108/a-healthy-bundle



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

