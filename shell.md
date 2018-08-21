# Shell
## General

* Shows all available rake commands: `rake -T`
* Shows routes `rake routes`
* Runs a test file/directory `rake exec rspec spec/path/to/spec`
* Runs a specific test from a file `rake exec rspec spec/path/to/spec.rb:42`

## Migrations
* Creates a new migration: `rails generate migration add_something_to_something`
* Creates a new migration with types: `rails generate migration add_something_to_something something:string`

## Unfuck the db

* Loads from schema.rb: `rake db:reset`
* Loads from migrations: `rake db:drop db:create db:migrate db:seed`
* Undo last migration: `rake db:rollback`
* Postgres doesn't accept connections after hard reset, `brew services stop postgresql`, check `/usr/local/var/postgres/postmaster.pid` and delete it if it exists, `brew services start postgresql`

## Heroku

* Open a rails console against production/staging: `heroku run rails -a ________`
