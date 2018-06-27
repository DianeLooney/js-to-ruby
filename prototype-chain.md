# Prototype Chain

http://leohetsch.com/include-vs-prepend-vs-extend/

In javascript, the concept of a prototype chain shows how properties of objects resolve to values.

In ruby, the lookup chain can be seen by `ClassName.ancestors`

There is also more control given to the developer for controlling the ancestors. The three ways to modify the ancestors are:
* Include
* Prepend
* Extend

## Include
Include is used to add an ancestor.
```ruby
module Logs
  def log(message)
    puts "[Logger]:#{message}"
  end
end
class Service
  include Logs
  
  def run()
    log("Run starts")
    
    log("Run ends")
  end
end
Service.ancestors # [Service, Logs, Object, Kernel, BasicObject]
```
In this case, the ancestors has a new entry, `Logs` just after the `Service` class. Therefore, `include` is good to add funcitonality to classes that we might want to override ourselves. It also keeps it easy to adjust the behavior of our mixins, since we can adjust whatever methods we need while still keeping the rest of the functionality the same.

Multiple includes push mixins further down the chain. So if two mixins have conflicting property names, the one included last will trump the others.

## Prepend
Prepend is used to push to the head of the ancestors.
```ruby
module Logs
  def log(message)
    puts "[Logger]:#{message}"
  end
  def run()
    log 'About to call run()'
    retval = super
    log 'Done calling run()'
    return retval
  end
end
class Service
  prepend Logs
  def log(message)
    puts "I will not run"
  end
  def run()
    log("Run starts")
    
    log("Run ends")
  end
end
Service.ancestors # [Logs, Service, Object, Kernel, BasicObject]
s = Service.new
s.run
# [Logger]:About to call run()
# [Logger]:Run starts
# [Logger]:Run ends
# [Logger]:Done calling run()
```
In this case, we see that the prepended module can wrap and override funcitonality. Notice that since the `log` method of `Logs` doesn't have a super call, the `log` method of `Service` will never be called. Ont he other hand, `run` has a `super` call, so it will execute the `run` method of Service. This can be useful for debugging, for ensuring that a method only runs under certain conditions, for ensuring a method never runs, to clean arguments, to make sure any errors from a function get caught, etc.

## Extend
```ruby
# Example 1

class Logs
  def self.log(message)
    puts "[Logger (class)]:#{message}"
  end
  def self.run()
    puts 'I was called by the super in Service.run'
  end
end

class Service < Logs
  def log(message)
    puts "[Logger (instance)]:#{message}"
  end
  def run()
    puts 'run() called on an instance of Service'
  end
  def self.run()
    puts 'Service.run called'
    super
  end
end
Service.ancestors # [Service, Logs, Object, Kernel, BasicObject]
Service.run()
# Service.run called
# I was called by the super in Service.run
s = Service.new
s.run # run() called on an instance of Service
Service.log 'Im logging something!' # Logger (class)]:Im logging something!
s.log 'Im logging something too!' # [Logger (instance)]:Im logging something too!
```
