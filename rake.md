# Rake tricks
## General

* Shows all available rake commands: `rake -T`
* Shows routes `rake routes`
* Runs a test file/directory `rake exec rspec spec/path/to/spec`
* Runs a specific test from a file `rake exec rspec spec/path/to/spec.rb:42`

## Unfuck the db

* Loads from schema.rb: `rake db:reset`
* Loads from migrations: `rake db:drop db:create db:migrate db:seed`
* Undo last migration: `rake db:rollback`
