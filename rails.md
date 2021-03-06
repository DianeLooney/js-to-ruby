# Rails Overview
## Ruby Phrases
* Solidus - ecommerce gem
* Easypost - shipping gem, integrated into solidus
* Spree - ecommerce platform, the upstream of solidus, a lot of solidus code will be Spree ns
* JSONAPI::Resource - class that defines an API endpoint’s behavior, CRUD-ish

## Patterns
Database binding is handled by schema.rb

Modifying schema.rb is done with a db migration

There is a tool to generate db migrations, and to apply them

Rails implements MVC

*Models* are classes, instances of each class correspond to a row of a table usually
* Models that extend ActiveRecord usually behave similarly
* ActiveRecords have a reload method to refresh the row contents from the db
* To modify an ActiveRecord, you must specifically update it with a method
* ActiveRecord singletons have helper methods to get things by id, by an index, or to create new instances
* (c/o specific) as long as contentful data is cached, it should be treated as read-only data

*Views* are implemented as cells
* Cells consist of a template file, a cell controller, and optional dependencies
* The template file is `*/*.slim`
* The controller is `*_controller.rb`
* The optional dependencies are `*/*.[scss|js]`
* Cells can have multiple templates, usually from `[show|index|edit]`
* Cell controllers are not the typical C in MVC, but simply helpers to make sure the templates get rendered with the data they need
* Cells can drop in react components from the javascript library. Some cells are completely empty aside from the element to host the react component

*Controllers* are implemented with controllers

* One of the common patterns is to define a common mutation as a class (perhaps complete checkout, register user, complete survey)
* An instance of that class represents a single mutation
* The properties required by the mutation are passed to `perform`
* `perform` executes the mutation, and is wrapped by `perform_async` to execute it in another thread

*Administrate* is an admin dashboard tool.
Generally, if you just need to get a quick admin interface up, it will be good for that. Lots of code generation and easy customization

*Assets* are stored in multiple places.
* `app/assets` is for application-specific assets
* `lib/assets` are for assets that are related closely to the app, but not integral
* `vendor/assets` are for modifying how gems look

*Routing*

`config/routes.rb`

There is a rake command to see everything getting routed by rails.

## Debug
* puma.rb
```ruby
if ENV.fetch('RAILS_ENV') == 'development'
  puts "LOGGER: development => worker_timeout 3600"
  worker_timeout 3600
end
```
