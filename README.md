[![Gem Version](https://badge.fury.io/rb/schema_plus_pg_types.svg)](http://badge.fury.io/rb/schema_plus_pg_types)
[![Build Status](https://secure.travis-ci.org/SchemaPlus/schema_plus_pg_types.svg)](http://travis-ci.org/SchemaPlus/schema_plus_pg_types)
[![Coverage Status](https://img.shields.io/coveralls/SchemaPlus/schema_plus_pg_types.svg)](https://coveralls.io/r/SchemaPlus/schema_plus_pg_types)
[![Dependency Status](https://gemnasium.com/SchemaPlus/schema_plus_pg_types.svg)](https://gemnasium.com/SchemaPlus/schema_plus_pg_types)

# SchemaPlus::PgTypes

SchemaPlus::PgTypes adds better support for PostgreSQL-specific types to
ActiveRecord, mapping them to higher-level types instead of raw strings.
Currently this only includes the PostgreSQL `interval` type, which is mapped
to `ActiveSupport::Duration`.

## Installation

<!-- SCHEMA_DEV: TEMPLATE INSTALLATION - begin -->
<!-- These lines are auto-inserted from a schema_dev template -->
As usual:

```ruby
gem "schema_plus_pg_types"                # in a Gemfile
gem.add_dependency "schema_plus_pg_types" # in a .gemspec
```

<!-- SCHEMA_DEV: TEMPLATE INSTALLATION - end -->


## Compatibility

SchemaPlus::PgTypes is tested on:

<!-- SCHEMA_DEV: MATRIX - begin -->
<!-- These lines are auto-generated by schema_dev based on schema_dev.yml -->
* ruby **2.3.1** with activerecord **5.0**, using **postgresql**

<!-- SCHEMA_DEV: MATRIX - end -->

## Usage

This gem adds a little more syntactic sugar for defining PostgreSQL types
in your migrations. You can now simply write: 

```ruby
create_table :events do |t|
  t.interval :event_duration
end
````

Instead of:

```ruby
create_table :events do |t|
  t.column :event_duration, :interval
end
```

The `event_duration` column will be represented as `ActiveSupport::Duration`
in your model, so you should be able to use it without the usual fuss:

```ruby
long_events = Event.where(1.hours..10.hours)
````

SchemaPlus::PgTypes is part of the [SchemaPlus](https://github.com/SchemaPlus/) family of Ruby on Rails ActiveRecord extension gems.


## History

* 0.1.1 - Improve test coverage (no change to production code)
* 0.1.0 - Initial release

## Development & Testing

Are you interested in contributing to SchemaPlus::PgTypes?  Thanks!  Please follow
the standard protocol: fork, feature branch, develop, push, and issue pull
request.

Some things to know about to help you develop and test:

<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_DEV - begin -->
<!-- These lines are auto-inserted from a schema_dev template -->
* **schema_dev**:  SchemaPlus::PgTypes uses [schema_dev](https://github.com/SchemaPlus/schema_dev) to
  facilitate running rspec tests on the matrix of ruby, activerecord, and database
  versions that the gem supports, both locally and on
  [travis-ci](http://travis-ci.org/SchemaPlus/schema_plus_pg_types)

  To to run rspec locally on the full matrix, do:

        $ schema_dev bundle install
        $ schema_dev rspec

  You can also run on just one configuration at a time;  For info, see `schema_dev --help` or the [schema_dev](https://github.com/SchemaPlus/schema_dev) README.

  The matrix of configurations is specified in `schema_dev.yml` in
  the project root.


<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_DEV - end -->

<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_PLUS_CORE - begin -->
<!-- These lines are auto-inserted from a schema_dev template -->
* **schema_plus_core**: SchemaPlus::PgTypes uses the SchemaPlus::Core API that
  provides middleware callback stacks to make it easy to extend
  ActiveRecord's behavior.  If that API is missing something you need for
  your contribution, please head over to
  [schema_plus_core](https://github.com/SchemaPlus/schema_plus_core) and open
  an issue or pull request.

<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_PLUS_CORE - end -->

<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_MONKEY - begin -->
<!-- These lines are auto-inserted from a schema_dev template -->
* **schema_monkey**: SchemaPlus::PgTypes is implemented as a
  [schema_monkey](https://github.com/SchemaPlus/schema_monkey) client,
  using [schema_monkey](https://github.com/SchemaPlus/schema_monkey)'s
  convention-based protocols for extending ActiveRecord and using middleware stacks.

<!-- SCHEMA_DEV: TEMPLATE USES SCHEMA_MONKEY - end -->
