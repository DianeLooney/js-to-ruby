# Arrays
## Basic
* length: `arr.length` and `arr.count`
* `arr.empty?
* includes: `arr.include? 'something'`
* push: `arr.push x`
* pop: `arr.pop`
* unshift: `arr.unshift x`
* shift: `arr.pop`

## pipeline
Note that `arr.someOperation(&:something)` and `arr.someOperation { |x| x.something }` are interchangeable

In general, adding an `!` to the end of a method makes it modify the original array
* filter: `arr.select { |x| x.something == 'something' }
* filter-opposite: `arr.reject`
* map: `arr.map { |x| x.something }
* first that satisfies condition: `arr.detect { |x| x.something }
* first `n` elements: `arr.take(n)`
* All but first `n` elements: `arr.drop(n)`
* `arr.compact` removes nils
* deduplicate by value: `arr.uniq`
* deduplicate by property: `arr.uniq(&:id)`
* concat: `arr1 + arr2` or `arr1.concat(arr2)
* forEach: `arr.each { |x| puts x.inspect }`
* flatten completely: `arr.flatten`
* flatten `n` levels: `arr.flatten(n)`
* indexOf: `arr.index(value)` or `arr.index { |x| x.something == 'value' }`
* permutations of size `n`: `arr.permutation(n)`
* all pairs of `[x,y]` with `x` from `arr1` and `y` from `arr2`: `arr1.product(arr2)`
* slice: `arr.slice`
* sort: `arr.sort(&:id)` and `arr.sort { |x,y| y.something <=> x.something }`
* zip: `arr1.zip(arr2)`
