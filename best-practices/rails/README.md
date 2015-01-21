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
