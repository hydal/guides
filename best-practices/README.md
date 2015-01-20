Best Practices
==============

A guide for programming well.

* [General](/best-practices/general)
* [Object-Oriented Design](/best-practices/object-oriented-design)





NodeJS
------

* Prefer to use modules as a way of dividing up code by functionality.
* Use `module.exports` to only provide access to methods required.
* Use the two frameworks [Express.JS] & [Restify] only.
* Use ES6 over ES5 with [Tracer] to handle coversion.

[Express.JS]: http://expressjs.com/
[Restify]: http://mcavage.me/node-restify/
[Tracer]: https://github.com/google/traceur-compiler



Ruby
----

* Avoid optional parameters. Does the method do too much?
* Avoid monkey-patching.
* Generate necessary [Bundler binstubs] for the project, such as `rake` and
`rspec`, and add them to version control.
* Prefer classes to modules when designing functionality that is shared by
multiple models.
* Prefer `private` when indicating scope. Use `protected` only with comparison
methods like `def ==(other)`, `def <(other)`, and `def >(other)`.

[Bundler binstubs]: https://github.com/sstephenson/rbenv/wiki/Understanding-binstubs

Ruby Gems
---------

* Declare dependencies in the `<PROJECT_NAME>.gemspec` file.
* Reference the `gemspec` in the `Gemfile`.
* Use [Appraisal] to test the gem against multiple versions of gem dependencies
(such as Rails in a Rails engine).
* Use [Bundler] to manage the gem's dependencies.
* Use [Travis CI] for Continuous Integration, indicators showing whether GitHub
pull requests can be merged, and to test against multiple Ruby versions.

[Appraisal]: https://github.com/thoughtbot/appraisal
[Bundler]: http://bundler.io
[Travis CI]: http://travis-ci.org

Rails
-----

* Avoid bypassing validations with methods like `save(validate: false)`, `update_attribute`, and `toggle`.
* Avoid instantiating more than one object in controllers.
* Avoid naming methods after database columns in the same class.
* Don't change a migration after it has been merged into master if the desired
change can be solved with another migration.
* Don't reference a model class directly from a view.
* Don't return false from `ActiveModel` callbacks, but instead raise an
exception.
* Don't use instance variables in partials. Pass local variables to partials
from view templates.
* Don't use SQL or SQL fragments (`where('inviter_id IS NOT NULL')`) outside of
models.
* Generate necessary [Spring binstubs] for the project, such as `rake` and
`rspec`, and add them to version control.
* If there are default values, set them in migrations.
* Keep `db/schema.rb` or `db/development_structure.sql` under version control.
* Use only one instance variable in each view.
* Use SQL, not `ActiveRecord` models, in migrations.
* Use the [`.ruby-version`] file convention to specify the Ruby version and
patch level for a project.
* Use `_url` suffixes for named routes in mailer views and [redirects].  Use
`_path` suffixes for named routes everywhere else.
* Validate the associated `belongs_to` object (`user`), not the database column
(`user_id`).
* Use `db/seeds.rb` for data that is required in all environments.
* Use `dev:prime` rake task for development environment seed data.
* Prefer `cookies.signed` over `cookies` to [prevent tampering].
* Prefer `Time.current` over `Time.now`
* Prefer `Date.current` over `Date.today`
* Prefer `Time.zone.parse("2014-07-04 16:05:37")` over `Time.parse("2014-07-04 16:05:37")`
* Use `ENV.fetch` for environment variables instead of `ENV[]`so that unset
environment variables are detected on deploy.

[`.ruby-version`]: https://gist.github.com/fnichol/1912050
[redirects]: http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.30
[Spring binstubs]: https://github.com/sstephenson/rbenv/wiki/Understanding-binstubs
[prevent tampering]: http://blog.bigbinary.com/2013/03/19/cookies-on-rails.html


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



JavaScript
----------

* Avoid using frameworks.
* Avoid using promises over callbacks (they are slower).
* Don't use JQuery or any library that relies on JQuery.
* Prefer using a series of libraries over a framework.
* Use ES6 over ES5 with [Tracer] to handle conversion
* Use Google's [Closure-Compiler] to remove dead-code from files.

[Tracer]: https://github.com/google/traceur-compiler
[Closure-Compiler]: https://developers.google.com/closure/compiler/


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

