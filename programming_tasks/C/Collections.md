[1]: https://rosettacode.org/wiki/Collections

# [Collections][1]

Arrays are ordered, integer-indexed collections of any object.

```ruby
# creating an empty array and adding values
var a = []          #=> []
a[0] = 1            #=> [1]
a[3] = "abc"        #=> [1, nil, nil, "abc"]
a << 3.14           #=> [1, nil, nil, "abc", 3.14]
```


A Hash is a dictionary-like collection of unique keys and their values. Also called associative arrays, they are similar to Arrays, but where an Array uses integers as its index, a Hash allows you to use any object type, which is automatically converted into a String.

```ruby
# creating an empty hash
var h = Hash()    #=> Hash()
h{:foo} = 1       #=> Hash("foo"=>1)
h{:bar} = 2.4     #=> Hash("foo"=>1, "bar"=>2.4)
h{:bar} += 3      #=> Hash("foo"=>1, "bar"=>5.4)
```


A Pair is an array-like collection, but restricted only to two elements.

```ruby
# create a simple pair
var p = Pair('a', 'b')
say p.first;            #=> 'a'
say p.second;           #=> 'b'
 
# create a pair of pairs
var pair = 'foo':'bar':'baz':();   # => Pair('foo', Pair('bar', Pair('baz', nil)))
 
# iterate over the values of a pair of pairs
loop {
    say pair.first;                #=> 'foo', 'bar', 'baz'
    pair = pair.second;
    pair == nil && break;
}
```


A Struct is a convenient way to bundle a number of attributes together.

```ruby
# creating a struct
struct Person {
    String name,
    Number age,
    String sex
}
 
var a = Person("John Smith", 41, :man)
 
a.age += 1                  # increment age
a.name = "Dr. #{a.name}"    # update name
 
say a.name          #=> "Dr. John Smith"
say a.age           #=> 42
say a.sex           #=> "man"
```