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
